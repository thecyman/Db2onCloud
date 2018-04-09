---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-15"

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Introdução
{: #getting_started_db2oncloud}

O {{site.data.keyword.Db2_on_Cloud_long}} é um banco de dados SQL provisionado para você na nuvem. É possível usar o {{site.data.keyword.Db2_on_Cloud_short}} da mesma forma que usaria qualquer software de banco de dados, mas sem o gasto adicional e a despesa de configuração de hardware e instalação e manutenção de software. 
{: shortdesc}

Também é possível instalar um banco de dados local do Db2 usando o [download gratuito do Db2 Developer Edition ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions). Ele instala rapidamente uma edição do desenvolvedor pronta para execução do Db2 com ferramentas dentro de um contêiner do Docker (o Docker não é necessário; qualquer componente necessário será instalado automaticamente). 

<!-- ## Free trial
{: #freetrial}

You can try the {{site.data.keyword.Db2_on_Cloud_short}} Precise Performance 500 (2.8.500) plan for 7 days on {{site.data.keyword.Bluemix_notm}} without charge. [Free trial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/db2){:new_window} -->

## Interfaces
{: #interfaces}

É possível trabalhar com o seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} das maneiras a seguir:
{: shortdesc}

   * Console da Web do {{site.data.keyword.Db2_on_Cloud_short}}
   * API do REST
   * Conecte aplicativos ou suas ferramentas favoritas por meio do seu computador local
   * Use o {{site.data.keyword.Db2_on_Cloud_short}} como uma origem de dados para seus apps ou serviços {{site.data.keyword.Bluemix_notm}}

### Console da web do Db2 on Cloud
{: #web_console}

O console da web fornece uma interface gráfica para tudo o que precisar para usar seu banco de dados, incluindo: instalações de carga, um editor de SQL, downloads de driver e mais.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

É possível acessar o seu console da web do {{site.data.keyword.Db2_on_Cloud_short}} das maneiras a seguir:
   * No painel do {{site.data.keyword.Bluemix_notm}}: é possível abrir o console da web por meio da página Detalhes do serviço para seu serviço do {{site.data.keyword.Db2_on_Cloud_long_notm}}.
   * URL direta: é possível marcar como favorita a URL do console da web para seu serviço do {{site.data.keyword.Db2_on_Cloud_short}}.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

### Conecte aplicativos ou suas ferramentas favoritas por meio do seu computador local
{: #connect_apps}

Configure seu ambiente local para se conectar ao seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} concluindo as etapas a seguir:
{: shortdesc}

1. Faça download do [pacote de drivers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} na página de informações sobre conexão do console da web do {{site.data.keyword.Db2_on_Cloud_short}}.
2. [Instale o pacote de drivers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} no computador em que seus apps ou ferramentas estão em execução.
3. [Configure os arquivos de drivers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} para seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}}.

### Use o Db2 on Cloud como uma origem de dados para os seus apps ou serviços do {{site.data.keyword.Bluemix_notm}}
{: #data_src}

Os apps hospedados no {{site.data.keyword.Bluemix_notm}} podem conectar-se ao seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} exatamente da mesma maneira que os seus aplicativos locais se conectam ao seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}}.
{: shortdesc}

Quando seus apps usam a plataforma {{site.data.keyword.Bluemix_notm}}, é possível aproveitar a variável de ambiente `VCAP _SERVICES` para simplificar a tarefa de especificar detalhes e credenciais do banco de dados:
1. Em seu painel do {{site.data.keyword.Bluemix_notm}}, na guia **Conexões** da página Detalhes do serviço para seu serviço do {{site.data.keyword.Db2_on_Cloud_long_notm}}, clique no botão **Criar conexão**.
2. Selecione o app do {{site.data.keyword.Bluemix_notm}} para usar com seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} como uma origem de dados e, em seguida, clique no botão **Conectar**.
3. Atualize seu código do aplicativo para recuperar detalhes e credenciais do banco de dados por meio da variável de ambiente `VCAP_SERVICES`:

    **Exemplo sem `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Get these database details from
    $hostname    = "<Host-name>";   # the Connect page of the Db2 on Cloud
    $port        = 50000;           # web console.
    $user        = "<User-ID >";    #
    $password    = "<Password>";    #
    $dsn         = "DATABASE=$database;" .
                   "HOSTNAME=$hostname;" .
                   "PORT=$port;" .
                   "PROTOCOL=TCPIP;" .
                   "UID=$user;" .
                   "PWD=$password;";

    $conn_string = $driver . $dsn;

    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

    **Exemplo com `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## Amostra
{: #samples}

Aqui estão links para amostras que demonstram como se conectar a seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} por meio de aplicativos em diferentes idiomas:
{: shortdesc}

   * [.NET ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
   * [Amostras do {{site.data.keyword.Db2_on_Cloud_short}} no GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window}


