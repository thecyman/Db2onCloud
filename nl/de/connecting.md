---

copyright:
  years: 2014, 2019
lastupdated: "2018-03-21"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Verbindung herstellen
{: #connect}

Sie können eine Verbindung von Befehlszeilenschnittstellen, von IBM® Anwendungen oder Tools, von Anwendungen oder Tools eines anderen Anbieters oder von Apps, die Sie erstellen, zu Ihrer Db2®-Datenbank herstellen. 
{: shortdesc}

## Voraussetzungen
{: #connect_prereq}

Falls beim Herstellen der Verbindung Probleme auftreten, stellen Sie sicher, dass die entsprechenden [Voraussetzungen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:new_window} erfüllt sind.
{: shortdesc}

### Umgebung konfigurieren
{: #cfg_env}

Wenn Sie lokale Anwendungen und Tools mit der Db2-Datenbank verbinden möchten, müssen Sie [die Umgebung konfigurieren![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}. 
{: shortdesc}

## Programmgestützte Verbindungsherstellung
{: #conx_prgrm}

Für die Erstellung von Anwendungen, die eine Verbindung mit einer Db2-Datenbank herstellen, können die gängigen Programmiersprachen verwendet werden.
{: shortdesc}

<!--* [Java ![External link icon](../../icons/launch-glyph.svg "External link icon"){}{:new_window} -->
* [JDBC ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
* [ODBC ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:new_window}
* [.NET ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
* [PHP ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}

## Verbindung für Apps und Tools herstellen
{: #conx_apps_tools}

Sie können auch externe Anwendungen und Tools mit {{site.data.keyword.Db2_on_Cloud_short}} verbinden und diese nutzen, um zusätzliche Verwaltungs- und Analyseaktionen für Ihre Daten durchzuführen. Beispiele:
   * Verbindung Ihrer {{site.data.keyword.Bluemix_short}}-Anwendungen, die eine Analysedatenbank benötigen.
   * [Verbindung von {{site.data.keyword.DSX_full}} (früher als IBM Data Science Experience bezeichnet). ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:new_window}
   * [Verbindung mit {{site.data.keyword.IBM_notm}} InfoSphere® Data Architect für den Entwurf und die Bereitstellung des Datenbankschemas. ![>Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:new_window}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [Verbindung eines {{site.data.keyword.IBM_notm}} Cognos®-Servers zur Ausführung von Cognos-Berichten für Ihre Daten. ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:new_window}
   * Verbindung mit SQL-basierten Tools wie Tableau oder Microsoft Excel für die Datenbearbeitung, -analyse oder -visualisierung. 
       * [Tableau ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:new_window}
       * [Microsoft Excel ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:new_window}
   * [Verbindung mit Aginity Workbench für die Migration von Netezza®-Datenmodellen und -Daten in {{site.data.keyword.dashdbshort_notm}}. ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:new_window}
