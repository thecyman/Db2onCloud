---

copyright:
  years: 2014, 2018
lastupdated: "2018-09-18"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Identity and Access Management (IAM) no IBM Cloud
{: #iam}

O Identity and Access Management (IAM) permite autenticar os usuários com segurança para os serviços da plataforma
e controlar consistentemente o acesso a recursos na plataforma do {{site.data.keyword.Bluemix_notm}}. Por
exemplo, com apenas um único login para o {{site.data.keyword.Bluemix_notm}} com o IBMid, você tem acesso
a qualquer um dos consoles de serviço e seus aplicativos sem precisar efetuar login em cada um deles separadamente.
{: shortdesc}

## O IAM está ativado na instância?
{: #enabled}

Durante um período de tempo, as instâncias de banco de dados gerenciadas do
{{site.data.keyword.Db2_on_Cloud_long}} no {{site.data.keyword.Bluemix_notm}} serão ativadas para usar
o controle de acesso do IAM. Para verificar se o IAM está ativado na instância, execute a consulta a seguir:

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

Se o valor retornado de **IAM_ENABLED** for 1, o IAM estará ativado na instância.

## Recursos do IBM Cloud IAM
{: #features}

Os seguintes recursos do IAM são implementados para o serviço
gerenciado do {{site.data.keyword.Db2_on_Cloud_short}} com dois tipos de identidades suportadas:

**ID IBM**

Os usuários com um IBMid devem ser incluídos em cada instância de serviço de banco de dados pelo administrador de banco de dados por meio do console ou da API de REST antes que esses usuários possam se conectar à instância de serviço de banco de dados específica. Assim como para um usuário não IBMid, uma identificação de usuário para a instância de serviço de banco de dados deve ser inserida ao mesmo tempo que o usuário IBMid é incluído. Essa identificação de usuário precisa ser exclusiva dentro da instância de serviço de banco de dados. Essa identificação de usuário também é o ID da autorização (AUTH) dentro do banco de dados. O administrador de banco de dados pode conceder e revogar permissões com base no ID de autorização.

**IDs de serviço**

Um ID de serviço identifica um serviço ou um aplicativo semelhante a como um ID de usuário identifica um usuário. Os IDs de serviço são IDs que podem ser usados pelos aplicativos para autenticação em um serviço do IBM Cloud. Um ID de serviço representa uma entidade separada do IBMid proprietário. Portanto, diferentes autoridades e permissões específicas podem ser concedidas ao ID de serviço dentro do banco de dados. Os IDs de serviço não têm senhas. Uma chave API deve ser criada para cada ID de serviço para que ele se conecte à instância de serviço de banco de dados. Para obter mais informações sobre os IDs de serviço, consulte: [Introduzindo os IDs de serviço e as chaves API do IBM Cloud IAM ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}.

## Conexões do cliente e logins do usuário
{: #connect}

**Pré-requisito**: Db2 Client V11.1 FP3 e mais recente.

Os métodos a seguir podem ser usados para a autenticação do IAM:

**Token de Acesso**

Um token de acesso pode ser obtido do serviço do IAM diretamente pelo aplicativo por meio da API de REST usando uma chave API. Para obter mais informações, consulte: [Obtendo um token do IBM Cloud IAM usando uma chave API ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}. O token de acesso tem um período de validade padrão de 60 minutos antes de expirar. Se o token tiver expirado, o servidor Db2 não permitirá que a conexão seja estabelecida. O token não é verificado quanto à expiração após a conexão ser estabelecida. Assim como era antes da integração do IAM, a conexão permanecerá conectada até que o aplicativo se desconecte ou a conexão seja finalizada devido a outros motivos.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

Um token de acesso identifica um usuário IBMid ou um ID de serviço para o banco de dados. O servidor de banco de dados verifica a validade do token de acesso antes de aceitá-lo. Esse é o melhor método se o aplicativo precisar se conectar a mais de uma instância de serviço de banco de dados ou a outras instâncias de serviço do {{site.data.keyword.Bluemix_notm}} porque ele minimiza a comunicação com o serviço do IAM para validar o token de acesso.

**Chave API**

Múltiplas chaves API podem ser criadas para cada usuário IBMid ou ID do serviço. Geralmente, cada chave API é criada para um único aplicativo. Ela
permite que o aplicativo se conecte à instância de serviço de banco de dados, desde que o IBMid proprietário ou o ID
de serviço seja incluído como um usuário na mesma instância de serviço de banco de dados. A chave API tem
as mesmas autoridades e permissões no banco de dados que o IBMid proprietário ou o ID de serviço. Caso um aplicativo não
deva mais ter permissão para se conectar ao banco de dados, a chave API correspondente pode ser removida. Esse método
de autenticação requer menos mudanças no aplicativo do que o uso de um token de acesso, pois não necessita de nenhuma
interação direta com o serviço do IAM. Para obter mais informações sobre a criação e o gerenciamento de chaves API, consulte:
[Gerenciando as chaves API do usuário
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}.

**IBMid/senha**

O IBMid/senha pode ser usado para efetuar login no console e também dentro do aplicativo das mesmas
formas que uma identificação de usuário/senha é permitida. A exceção ocorre quando o IBMid é federado porque um redirecionamento
para a página de login da sua organização não pode ser feito. No entanto, o método recomendado para um aplicativo
estabelecer uma conexão com a instância de serviço de banco de dados é usar um token de acesso.

## Interfaces suportadas
{: #sup-if}

As interfaces do cliente de banco de dados a seguir são suportadas:

* [ODBC](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC e CLPPLUS
{: #odbc-clpplus}

Para que um aplicativo ODBC ou um cliente da linha de comandos (CLPPLUS) se conecte a um servidor Db2 usando a
autenticação do IAM, um nome de origem de dados (DSN) precisa ser configurado primeiro em um arquivo de configuração `db2dsdriver.cfg` executando o comando a seguir:

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

O arquivo de configuração `db2dsdriver.cfg` é um arquivo XML, geralmente localizado no diretório
`sqllib/cfg`, que contém uma lista de aliases do DSN e suas propriedades.

O exemplo a seguir de um arquivo de configuração `db2dsdriver.cfg` mostra as configurações que são usadas para estabelecer uma conexão com uma instância de serviço de banco de dados. O
arquivo de configuração fornece o alias do DSN, o nome do banco de dados, o nome do host (ou o endereço IP) e o tipo de **Autenticação** e os valores de parâmetro **SecurityTransportMode**:

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<configuration>
        <dsncollection>
        <dsn alias="<data_source_name>" name="bludb" host="<host_name_or_IP_address>" port="50001">
            <parameter name="Authentication" value="GSSPLUGIN"/>
            <parameter name="SecurityTransportMode" value="SSL"/>
        </dsn>
        </dsncollection>
        <databases>
            <database name="bludb" host="<host_name_or_IP_address>" port="50001"/>
        </databases>
</configuration>
```

* A sequência de conexão ODBC pode conter um dos seguintes:

    **Token de Acesso**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **Chave API**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBMid/senha**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    Para o ODBC, o **AUTHENTICATION=GSSPLUGIN** pode ser especificado no arquivo de
configuração `db2dsdriver.cfg` ou na sequência de conexão do aplicativo.

* O comando de conexão CLPPLUS pode conter um dos seguintes:

    **Token de Acesso**

    Conecte-se ao alias do DSN (`@<data_source_name>`) e transmita o token de acesso
executando o comando a seguir no prompt de comandos ou script CLPPLUS:

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **Chave API**

    Conecte-se ao alias do DSN (`@<data_source_name>`) com uma chave API executando o
seguinte comando no prompt de comandos ou script CLPPLUS:

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBMid/senha**

    Conecte-se ao alias do DSN (`@<data_source_name>`) com um IBMid/senha executando
o seguinte comando no prompt de comandos ou script CLPPLUS:

    `connect <IBMid>/<password>@<data_source_name>`

    Para obter mais detalhes sobre como se conectar ao aliases do DSN com o CLPPLUS, consulte: [Aliases do DSN no CLPPlus ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}.

### JDBC
{: #jdbc}

O driver JDBC Tipo 4 é suportado para a autenticação do IAM.

Os exemplos a seguir mostram os fragmentos da conexão para os três métodos:

**Token de Acesso**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setAccessToken( "<access_token>" );
Connection conn = dataSource.getConnection( );
```

**Chave API**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setApiKey( "<api_key>" );
Connection conn = dataSource.getConnection( );
```

**IBMid/senha**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<user_ID>", "<password>" );
```

## Experiência do usuário do console
{: #console-ux}

A página de login do console de serviço tem a opção de efetuar login com o IBMid e a senha. Depois de clicar no
botão **Conectar por meio do IBMid**, o usuário é direcionado para a página de login do IAM, na qual a
senha é inserida. Quando a autenticação for concluída, o usuário será redirecionado de volta para o console. Antes que o
login possa ser feito com êxito, o usuário com o IBMid deve ser incluído em cada instância de serviço de banco de dados
pelo administrador de banco de dados por meio do console ou da API de REST. Assim como para um usuário não IBMid, uma identificação de usuário para a instância de
serviço de banco de dados deve ser inserida ao mesmo tempo que o usuário IBMid é incluído. A identificação de usuário
precisa ser exclusiva dentro da instância de serviço de banco de dados. Essa identificação de usuário também é o ID da autorização (AUTH) dentro do banco
de dados.

## Experiência da API de REST
{: #api}

A API de REST do {{site.data.keyword.Db2_on_Cloud_short}} foi aprimorada para também aceitar um token
de acesso do IAM para as funções que anteriormente aceitavam um token de acesso gerado pelo serviço de banco de dados.

* Para incluir um novo usuário IBMid, execute a seguinte chamada API de exemplo:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  **Nota**: o `<userid>` valor para `"id"` e
`"ibmid"` não precisam ser os mesmos. Os dois IDs diferentes não são vinculados de nenhuma maneira.

* Para migrar um usuário de banco de dados não IBMid existente (por exemplo, `abcuser`) e
torná-lo um usuário IBMid, primeiro exclua a identificação de usuário não IBMid executando a seguinte chamada API de
exemplo:

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  Em seguida, inclua novamente o usuário com um IBMid que seja o mesmo que a identificação de usuário anterior (`abcuser`) executando a seguinte chamada API de exemplo:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Como a identificação de usuário (`abcuser`) permanece a mesma para o novo IBMid para este usuário, as
permissões de banco de dados concedidas para o usuário permanecem inalteradas. Se uma lista de usuários de banco de
dados não IBMid existente precisar ser migrada para torná-los usuários IBMid, será necessário executar o par
de chamadas API anterior para cada usuário.

* Para incluir muitos novos usuários IBMid de uma só vez, crie um arquivo em lote que liste as seguintes chamadas
API de exemplo, uma para cada usuário:

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

Para obter mais detalhes sobre a API de seu serviço, consulte:
[API de REST do {{site.data.keyword.Db2_on_Cloud_short}}
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://ibm.biz/db2oc_api){:new_window}.

## Federação do IBMid
{: #fed}

Para usar o seu próprio provedor de identidade, como o LDAP, deve-se primeiro federar o servidor LDAP
com o IBMid. Para obter instruções sobre como federar o servidor LDAP com o IBMid, consulte:
[IBMid Enterprise Federation
Adoption Guide ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}. Após a conclusão da federação do IBMid e da inclusão dos usuários permitidos na instância de serviço de banco de
dados pelo administrador de banco de dados, esses usuários poderão efetuar login no console com a identificação de
usuário e a senha de suas empresas. Alternativamente, esses usuários podem usar um token de acesso ou uma chave API que
represente a identificação de usuário para se conectar à instância de serviço de banco de dados por meio de uma das
interfaces suportadas do cliente de banco de dados.

## Restrictions
{: #restrictions}

A seguir estão as restrições quanto à autenticação do IAM:

* A autenticação do IAM para um cliente Db2 que está se conectando a um servidor Db2 é suportada apenas por
meio de uma conexão SSL.
* A federação do IBMid é suportada para permitir que o portal ou o servidor de gerenciamento de usuários
customizados seja usado para a autenticação. Esse suporte não inclui nenhuma federação de grupo.
* A autenticação do IAM para a federação de banco de dados não é suportada.
* A execução de comandos IDA e de extensão definida pelo usuário (UDX) por meio do CLPPlus não é suportada.
* O driver JDBC Tipo 2 não é suportado.




