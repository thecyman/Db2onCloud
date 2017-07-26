---

copyright:
  years: 2014, 2017
lastupdated: "2017-06-21"

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

#Einführung in Db2 on Cloud (früher dashDB for Analytics)
{: #getting_started_db2oncloud}

Bei {{site.data.keyword.Db2_on_Cloud_long}} handelt es sich um eine SQL-Datenbank, die für Sie in der Cloud bereitgestellt wird. Sie können {{site.data.keyword.Db2_on_Cloud_short}} wie jede andere Datenbanksoftware verwenden, der Aufwand und die Kosten für die Hardwareeinrichtung sowie die Softwareinstallation und -verwaltung fallen jedoch weg. 
{: shortdesc}

##Schnittstellen
{: #interfaces}

Für die Arbeit mit der {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank stehen Ihnen die folgenden Möglichkeiten zur Verfügung:
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}}-Webkonsole
<!--   * REST APIs -->
   * Herstellen einer Verbindung für Anwendungen oder bevorzugte Tools vom lokalen Computer
   * Verwenden von {{site.data.keyword.Db2_on_Cloud_short}} als Datenquelle für Bluemix-Apps oder -Services

###Db2 on Cloud-Webkonsole
{: #web_console}

Die Webkonsole bietet eine grafische Schnittstelle für alle Funktionen, die Sie für die Verwendung der Datenbank benötigen. Hierzu gehören z. B. Ladefunktionen, ein SQL-Editor, Treiberdownloads usw.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour "External link icon"){:new_window}. -->

Für den Zugriff auf die {{site.data.keyword.Db2_on_Cloud_short}}-Webkonsole stehen Ihnen die folgenden Möglichkeiten zur Verfügung:
   * Über das {{site.data.keyword.Bluemix_notm}}-Dashboard - Sie können die Webkonsole über die Servicedetailseite für Ihren {{site.data.keyword.Db2_on_Cloud_long_notm}}-Service öffnen.
   * Direkt über die URL - Sie können die URL der Webkonsole für Ihren {{site.data.keyword.Db2_on_Cloud_short}}-Service mit einem Lesezeichen markieren.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

###Herstellen einer Verbindung für Anwendungen oder bevorzugte Tools vom lokalen Computer
{: #connect_apps}

Führen Sie die folgenden Schritte aus, um die lokale Umgebung für die Verbindung zur {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank zu konfigurieren:
{: shortdesc}

1. Laden Sie das [-Treiberpaket ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html "Symbol für externen Link"){:new_window} von der Verbindungsinformationsseite der {{site.data.keyword.Db2_on_Cloud_short}}-Webkonsole herunter. 
2. [Installieren Sie das Treiberpaket ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html "Symbol für externen Link"){:new_window} auf dem Computer, auf dem Ihre Apps bzw. Tools ausgeführt werden.
3. [Konfigurieren Sie die Treiberdateien ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html "Symbol für externen Link"){:new_window} für Ihre {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank.

###Verwenden von Db2 on Cloud als Datenquelle für Bluemix-Apps oder -Services
{: #data_src}

Für Apps, die per Hosting in {{site.data.keyword.Bluemix_notm}} bereitgestellt werden, können Verbindungen zu Ihrer {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank auf dieselbe Weise hergestellt werden wie bei Verbindungen für lokalen Anwendungen zu Ihrer {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank.
{: shortdesc}

Wenn Ihre Apps die {{site.data.keyword.Bluemix_notm}}-Plattform verwenden, können Sie die Umgebungsvariable `VCAP _SERVICES` nutzen, um das Angeben von Datenbankdetails und -berechtigungsnachweisen zu vereinfachen:
1. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-Dashboard auf der Registerkarte **Verbindungen** der Servicedetailseite für Ihren {{site.data.keyword.Db2_on_Cloud_long_notm}}-Service auf die Schaltfläche **Verbindung erstellen**.
2. Wählen Sie die {{site.data.keyword.Bluemix_notm}}-App aus, die mit der {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank als Datenquelle verwendet werden soll, und klicken Sie dann auf die Schaltfläche **Verbinden**.
3. Aktualisieren Sie den Anwendungscode, um Datenbankdetails- und -berechtigungsnachweise aus der Umgebungsvariablen `VCAP_SERVICES` abzurufen.

    **Beispiel ohne `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Datenbankdetails von der
    $hostname    = "<Host-name>";   # Verbindungsseite der
    $port        = 50000;           # Db2 on Cloud-Webkonsole abrufen.
    $user        = "<Benutzer-ID >";    #
    $password    = "<Kennwort>";    #
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

    **Beispiel mit `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

##Beispiele
{: #samples}

Über die folgenden Links können Sie Beispiele aufrufen, die veranschaulichen, wie Sie eine Verbindung von Anwendungen in verschiedenen Sprachen zu Ihrer {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank herstellen:
{: shortdesc}

   * [.NET ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html "Symbol für externen Link"){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html "External link icon"){:new_window} -->
   * [JDBC ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html "Symbol für externen Link"){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html "External link icon"){:new_window} -->
   * [PHP ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html "Symbol für externen Link"){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html "External link icon"){:new_window} -->
   * [{{site.data.keyword.Db2_on_Cloud_short}}-Beispiele in GitHub ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld "Symbol für externen Link"){:new_window}


