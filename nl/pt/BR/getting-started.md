---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-30"

keywords: 

subcollection: Db2onCloud

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
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Tutorial de Introdução
{: #getting-started}

O {{site.data.keyword.Db2_on_Cloud_long}} é um banco de dados SQL que é provisionado para você na nuvem. É possível usar o {{site.data.keyword.Db2_on_Cloud_short}} do mesmo modo que você usaria qualquer software de banco de dados, mas sem o tempo e a despesa de configuração de hardware ou instalação e manutenção de software.
{: shortdesc}

Crie credenciais. Para aqueles que são novos no IBM Cloud, após criar o serviço, deve-se criar
um nome do usuário e senha clicando no botão **Criar credenciais** ao iniciar o
serviço. Tecnicamente, é possível efetuar login no console da web sem credenciais, mas você precisa
do nome do usuário e da senha para usar muitas das ferramentas do Db2.
{: important}

Também é possível instalar um banco de dados Db2 local usando o [download do Db2 Developer Edition grátis ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:new_window}. Ele instala rapidamente uma
edição de desenvolvedor pronta para desenvolvimento do Db2 com ferramentas dentro de um contêiner do
Docker (o Docker não é requerido; ele instala automaticamente quaisquer componentes necessários). 

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

### Instalando clientes de linha de comandos e drivers do Db2 em seu computador
{: #connect_apps}

Na maioria dos casos, os usuários tendem a usar apenas a API de REST ou
instalar drivers para uma estrutura, por exemplo, com o comando `pip` da Python.
{: shortdesc}

Para instalar pacotes de drivers Python para o MacOS, deve-se usar o comando `pip` com a opção `--no-cache-dir`. Para obter instruções detalhadas, veja: [Suporte do Python para IBM DB2 e IBM Informix ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2-drivers-python){:new_window}
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

Para instalar os drivers de estrutura Python ou Node.js, clique em um dos links a seguir:
- [Drivers Python ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2-drivers-python){:new_window}
- [Drivers Node.js ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://ibm.biz/db2-drivers-node){:new_window}

Para instalar o Node.js ORM denominado Sequelize, clique no link a seguir:
[Sequelize ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibmdb/sequelize){:new_window}
{: note}

Para obter mais opções de instalação do driver, incluindo Java, Go, Jupyter Notebooks, Ruby, PHP e mais, clique no link a seguir: 

- [ibmdb ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibmdb){:new_window}

Supondo que você já tenha instalado drivers de estrutura, é possível ignorar as etapas a seguir. No entanto, os usuários avançados podem desejar usar o cliente de linha de comandos do Db2 para administrar seu banco de dados e usar os comandos do Db2. Além disso, determinados aplicativos ODBC ou JDBC podem se beneficiar de uma instalação geral de
drivers do Db2. Se esse for o caso, conclua as etapas a seguir:

1. [Instale o pacote de drivers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} no computador em que seus apps ou ferramentas estão em execução.
2. [Configure os arquivos de drivers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} para seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}}.

### Use o Db2 on Cloud como uma origem de dados para os seus apps ou serviços do {{site.data.keyword.Bluemix_notm}}
{: #data_src}

Os apps que são hospedados no {{site.data.keyword.Bluemix_notm}} podem se conectar ao
seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} da mesma maneira que os
aplicativos locais se conectam ao seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}}.
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

Aqui estão os links para as amostras que demonstram como se conectar ao seu banco de dados do {{site.data.keyword.Db2_on_Cloud_short}} em aplicativos em diferentes idiomas:
{: shortdesc}

   * [.NET ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window} -->

## Vídeo: Introduzindo o Db2 on Cloud
{: #intro_vid}

Assista a este vídeo para ver uma introdução ao {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="Introdução ao {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Vídeo: Usando a API de REST para se comunicar com o Db2 on Cloud
{: #vid_api}

Assista a este vídeo para ver as etapas necessárias para usar uma API de RESTful para se comunicar com o {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer2" title="Usando a API de RESTful para se comunicar com o {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Vídeo: Integrando os Notebooks Jupyter
{: #cognos_vid}

Assista a este vídeo para ver como integrar os Notebooks Jupyter com o {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Integrando os blocos de notas do Jupyter" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


