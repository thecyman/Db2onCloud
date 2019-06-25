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

# 入门教程
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}} 是在云中为您供应的 SQL 数据库。您可以像使用任何数据库软件一样来使用 {{site.data.keyword.Db2_on_Cloud_short}}，但是却无需耗费时间和费用来设置硬件或进行软件安装和维护。
{: shortdesc}

创建凭证。对于那些刚接触 IBM Cloud 的人来说，在创建服务后还必须创建用户名和密码，方法是在启动服务时单击**创建凭证**按钮。从技术层面上讲，您可以在没有凭证的情况下登录到 Web 控制台，但是如果要使用一些 Db2 工具，就需要提供您的用户名和密码。
{: important}

您还可以通过[免费的 Db2 Developer Edition 下载 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:new_window} 来安装本地 Db2 数据库。这样可以快速安装随时可用的开发者版本的 Db2，其中 Db2 工具会包含在 Docker 容器中（无需安装 Docker，因为它会自动安装任何必要的组件）。 

## 界面
{: #interfaces}

您可以通过以下方法来使用 {{site.data.keyword.Db2_on_Cloud_short}} 数据库：
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} Web 控制台
   * REST API
   * 从本地计算机连接应用程序或喜爱的工具
   * 使用 {{site.data.keyword.Db2_on_Cloud_short}} 作为 {{site.data.keyword.Bluemix_notm}} 应用程序或服务的数据源

### Db2 on Cloud Web 控制台
{: #web_console}

Web 控制台为您需要使用数据库的所有项目提供图形界面，包括：装入功能、SQL 编辑器、驱动程序下载等。
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

您可以通过以下方法来访问 {{site.data.keyword.Db2_on_Cloud_short}} Web 控制台：
   * 从 {{site.data.keyword.Bluemix_notm}} 仪表板 - 您可以从 {{site.data.keyword.Db2_on_Cloud_long_notm}} 服务的“服务详细信息”页面打开 Web 控制台。
   * 直接 URL - 您可以针对 {{site.data.keyword.Db2_on_Cloud_short}} 服务为 Web 控制台的 URL 设置书签。

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

### 在计算机上安装 Db2 命令行客户机和驱动程序
{: #connect_apps}

在大多数情况下，用户都会倾向于仅使用 REST API，或者安装框架的驱动程序，例如使用 Python 的 `pip` 命令。
{: shortdesc}

要安装 MacOS 的 Python 驱动程序包，您必须使用带 `--no-cache-dir` 选项的 `pip` 命令。有关详细的指示信息，请参阅：[Python support for IBM DB2 and IBM Informix ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2-drivers-python){:new_window}
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

要安装 Python 或 Node.js 框架驱动程序，请单击以下其中一个链接：
- [Python 驱动程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2-drivers-python){:new_window}
- [Node.js 驱动程序 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2-drivers-node){:new_window}

要安装名为 Sequelize 的 Node.js ORM，请单击以下链接：[Sequelize ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibmdb/sequelize){:new_window}
{: note}

有关驱动程序安装选项（包括 Java、Go、Jupyter 配置页、Ruby、PHP 等）的更多信息，请单击以下链接： 

- [ibmdb ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/ibmdb){:new_window}

假定您已安装了框架驱动程序，那么可以跳过以下步骤。但是，高级用户可能还希望通过使用 Db2 命令行客户机来管理他们的数据库并使用 Db2 命令。此外，某些 ODBC 或 JDBC 应用程序也可以从 Db2 驱动程序的常规安装中受益。如果是这种情况，请完成以下步骤：


1. 在运行应用程序和工具的计算机上[安装驱动程序包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window}。
2. 为 {{site.data.keyword.Db2_on_Cloud_short}} 数据库[配置驱动程序文件 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}。

### 使用 Db2 on Cloud 作为 {{site.data.keyword.Bluemix_notm}} 应用程序或服务的数据源
{: #data_src}

可以使用与本地应用程序连接到 {{site.data.keyword.Db2_on_Cloud_short}} 数据库的相同方法，将在 {{site.data.keyword.Bluemix_notm}} 上托管的应用程序连接到 {{site.data.keyword.Db2_on_Cloud_short}} 数据库。
{: shortdesc}

当应用程序使用 {{site.data.keyword.Bluemix_notm}} 平台时，您可以利用 `VCAP _SERVICES` 环境变量来简化指定数据库详细信息和凭证的任务：
1. 在 {{site.data.keyword.Bluemix_notm}} 仪表板上，在 {{site.data.keyword.Db2_on_Cloud_long_notm}} 服务的“服务详细信息”页面的**连接**选项卡上，单击**创建连接**按钮。
2. 选择 {{site.data.keyword.Bluemix_notm}} 应用程序以使用 {{site.data.keyword.Db2_on_Cloud_short}} 数据库作为数据源，然后单击**连接**按钮。
3. 更新应用程序代码以从 `VCAP_SERVICES` 环境变量检索数据库详细信息和凭证：

    **没有 `VCAP_SERVICES` 的示例**

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

    **具有 `VCAP_SERVICES` 的示例**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## 样本
{: #samples}

以下是示例的链接，这些示例演示了在不同的语言中，如何从应用程序连接到 {{site.data.keyword.Db2_on_Cloud_short}} 数据库：
{: shortdesc}

   * [.NET ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window} -->

## 视频：介绍 Db2 on Cloud
{: #intro_vid}

观看此视频，了解 {{site.data.keyword.Db2_on_Cloud_short}} 简介。

<iframe class="embed-responsive-item" id="youtubeplayer1" title="简介：{{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## 视频：使用 REST API 与 Db2 on Cloud 通信
{: #vid_api}

观看此视频，了解使用 RESTful API 与 {{site.data.keyword.Db2_on_Cloud_short}} 通信的步骤。

<iframe class="embed-responsive-item" id="youtubeplayer2" title="使用 RESTful API 与之通信：{{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## 视频：集成 Jupyter 配置页
{: #cognos_vid}

观看此视频，了解如何将 Jupyter 配置页与 {{site.data.keyword.Db2_on_Cloud_short}} 相集成。

<iframe class="embed-responsive-item" id="youtubeplayer3" title="集成 Jupyter 配置页" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


