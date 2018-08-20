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

# Getting started
{: #getting_started_db2oncloud}

{{site.data.keyword.Db2_on_Cloud_long}} is an SQL database provisioned for you in the cloud. You can use {{site.data.keyword.Db2_on_Cloud_short}} just as you would use any database software, but without the hassles of hardware setup or software installation and maintenance. 

If you're deploying the free Lite plan from outside of continental North America, see: [Using the Lite plan outside continental North America](free_plan.html#outside_na){:new_window}.
{: shortdesc}

You can also install a local Db2 database using the [free Db2 Developer Edition download ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions). It rapidly installs a ready-to-go developer edition of Db2 with tools inside a Docker container (Docker not required; it will automatically install any necessary components). 

<!-- ## Free trial
{: #freetrial}

You can try the {{site.data.keyword.Db2_on_Cloud_short}} Precise Performance 500 (2.8.500) plan for 7 days on {{site.data.keyword.Bluemix_notm}} without charge. [Free trial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/db2){:new_window} -->

## Interfaces
{: #interfaces}

You can work with your {{site.data.keyword.Db2_on_Cloud_short}} database in the following ways:
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} web console
   * REST API
   * Connect applications or your favorite tools from your local computer
   * Use {{site.data.keyword.Db2_on_Cloud_short}} as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services

### Db2 on Cloud web console
{: #web_console}

The web console provides a graphical interface for everything that you need to use your database, including: load facilities, an SQL editor, driver downloads, and more.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

You can access your {{site.data.keyword.Db2_on_Cloud_short}} web console in the following ways:
   * From your {{site.data.keyword.Bluemix_notm}} dashboard - You can open the web console from the Service Details page for your {{site.data.keyword.Db2_on_Cloud_long_notm}} service.
   * Direct URL - You can bookmark the URL of the web console for your {{site.data.keyword.Db2_on_Cloud_short}} service.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

### Connect applications or your favorite tools from your local computer
{: #connect_apps}

Configure your local environment to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database by completing the following steps:
{: shortdesc}

1. Download the [driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.
2. [Install the driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} on the computer where your apps or tools are running.
3. [Configure the driver files ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} for your {{site.data.keyword.Db2_on_Cloud_short}} database.

### Use Db2 on Cloud as a data source for your {{site.data.keyword.Bluemix_notm}} apps or services
{: #data_src}

Apps hosted on {{site.data.keyword.Bluemix_notm}} can connect to your {{site.data.keyword.Db2_on_Cloud_short}} database exactly the same way that your local applications connect to your {{site.data.keyword.Db2_on_Cloud_short}} database.
{: shortdesc}

When your apps use the {{site.data.keyword.Bluemix_notm}} platform, you can take advantage of the `VCAP _SERVICES` environment variable to simplify the task of specifying database details and credentials:
1. On your {{site.data.keyword.Bluemix_notm}} dashboard, in the **Connections** tab of the Service Details page for your {{site.data.keyword.Db2_on_Cloud_long_notm}} service, click the **Create connection** button.
2. Select the {{site.data.keyword.Bluemix_notm}} app to use with your {{site.data.keyword.Db2_on_Cloud_short}} database as a data source, and then click the **Connect** button.
3. Update your application code to retrieve database details and credentials from the `VCAP_SERVICES` environment variable:

    **Example without `VCAP_SERVICES`**

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

    **Example with `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## Samples
{: #samples}

Here are links to samples demonstrating how to connect to your {{site.data.keyword.Db2_on_Cloud_short}} database from applications in different languages:
{: shortdesc}

   * [.NET ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
   * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window}

