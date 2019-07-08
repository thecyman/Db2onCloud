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

# 連接
{: #connect}

您可以將指令行、IBM® 或協力廠商應用程式或工具，或是您建立的應用程式，連接到您的 Db2® 資料庫。
{: shortdesc}

## 必要條件
{: #connect_prereq}

如果您在連接時有問題，請完成[必要條件](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:external}。
{: shortdesc}

### 配置環境
{: #cfg_env}

若要將本端應用程式及工具連接至 Db2 資料庫，您需要[配置環境](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external}。
{: shortdesc}

## 以程式設計方式連接
{: #conx_prgrm}

您可以使用一般程式設計語言來建立連接 Db2 資料庫的應用程式。
{: shortdesc}

<!--* [Java{}{:external} -->
* [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
* [ODBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:external}
* [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
* [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}

## 連接應用程式及工具
{: #conx_apps_tools}

您也可以將外部應用程式及工具連接至 {{site.data.keyword.Db2_on_Cloud_short}}，並使用它們來進一步管理或分析資料。例如：
   * 連接需要分析資料庫的 {{site.data.keyword.Bluemix_short}} 應用程式。
   * [從 {{site.data.keyword.DSX_full}}（先前稱為 IBM Data Science Experience）連接。](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:external}
   * [連接 {{site.data.keyword.IBM_notm}} InfoSphere® Data Architect，以設計及部署資料庫綱目。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:external}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [連接 {{site.data.keyword.IBM_notm}} Cognos® 伺服器，以針對您的資料執行 Cognos 報告。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:external}
   * 連接 SQL 工具，例如 Tableau 或 Microsoft Excel，以操作、分析或視覺化您的資料。 
       * [Tableau](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:external}
       * [Microsoft Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:external}
   * [連接 Aginity Workbench 以將 Netezza® 資料模型和資料移轉至 {{site.data.keyword.dashdbshort_notm}}。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:external}
