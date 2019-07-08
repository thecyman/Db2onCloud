---

copyright:
  years: 2014, 2019
lastupdated: "2018-03-21"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
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

Falls beim Herstellen der Verbindung Probleme auftreten, stellen Sie sicher, dass die entsprechenden [Voraussetzungen](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:external} erfüllt sind.
{: shortdesc}

### Umgebung konfigurieren
{: #cfg_env}

Wenn Sie lokale Anwendungen und Tools mit der Db2-Datenbank verbinden möchten, müssen Sie [die Umgebung konfigurieren](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external}.
{: shortdesc}

## Programmgestützte Verbindungsherstellung
{: #conx_prgrm}

Für die Erstellung von Anwendungen, die eine Verbindung mit einer Db2-Datenbank herstellen, können die gängigen Programmiersprachen verwendet werden.
{: shortdesc}

<!--* [Java{}{:external} -->
* [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
* [ODBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:external}
* [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
* [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}

## Verbindung für Apps und Tools herstellen
{: #conx_apps_tools}

Sie können auch externe Anwendungen und Tools mit {{site.data.keyword.Db2_on_Cloud_short}} verbinden und diese nutzen, um zusätzliche Verwaltungs- und Analyseaktionen für Ihre Daten durchzuführen. Beispiele:
   * Verbindung Ihrer {{site.data.keyword.Bluemix_short}}-Anwendungen, die eine Analysedatenbank benötigen.
   * [Verbindung von {{site.data.keyword.DSX_full}} (früher als IBM Data Science Experience bezeichnet).](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:external}
   * [Verbindung mit {{site.data.keyword.IBM_notm}} InfoSphere® Data Architect für den Entwurf und die Bereitstellung des Datenbankschemas.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:external}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [Verbindung eines {{site.data.keyword.IBM_notm}} Cognos®-Servers zur Ausführung von Cognos-Berichten für Ihre Daten.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:external}
   * Verbindung mit SQL-basierten Tools wie Tableau oder Microsoft Excel für die Datenbearbeitung, -analyse oder -visualisierung. 
       * [Tableau](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:external}
       * [Microsoft Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:external}
   * [Verbindung mit Aginity Workbench für die Migration von Netezza®-Datenmodellen und -Daten in {{site.data.keyword.dashdbshort_notm}}.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:external}
