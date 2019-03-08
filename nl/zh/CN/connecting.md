---

copyright:
  years: 2014, 2019
lastupdated: "2018-03-21"

keywords: 

subcollection: Db2onCloud

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

# 连接
{: #connect}

您可以将命令行界面、IBM® 或第三方应用程序或工具，或者自己创建的应用程序连接到 Db2® 数据库。
{: shortdesc}

## 先决条件
{: #connect_prereq}

如果无法连接，请完成[先决条件 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:new_window}。
{: shortdesc}

### 配置环境
{: #cfg_env}

要将本地应用程序和工具连接到 Db2 数据库，您需要[配置环境 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}。
{: shortdesc}

## 以编程方式连接
{: #conx_prgrm}

您可以使用常用编程语言来创建连接到 Db2 数据库的应用程序。
{: shortdesc}

<!--* [Java ![External link icon](../../icons/launch-glyph.svg "External link icon"){}{:new_window} -->
* [JDBC ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
* [ODBC ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:new_window}
* [.NET ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
* [PHP ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}

## 连接应用程序和工具
{: #conx_apps_tools}

您还可以将外部应用程序和工具连接到 {{site.data.keyword.Db2_on_Cloud_short}}，以使用其进一步管理或分析数据。例如：
   * 连接需要分析数据库的 {{site.data.keyword.Bluemix_short}} 应用程序。
   * [从 {{site.data.keyword.DSX_full}}（以前称为 IBM Data Science Experience）连接。![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:new_window}
   * [连接 {{site.data.keyword.IBM_notm}} InfoSphere® Data Architect，以设计和部署数据库模式。![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:new_window}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [连接 {{site.data.keyword.IBM_notm}} Cognos® 服务器，以对数据运行 Cognos 报告。![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:new_window}
   * 连接基于 SQL 的工具（如 Tableau 或 Microsoft Excel），以控制、分析或可视化数据。 
       * [Tableau ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:new_window}
       * [Microsoft Excel ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:new_window}
   * [连接 Aginity Workbench，以将 Netezza® 数据模型和数据迁移到 {{site.data.keyword.dashdbshort_notm}}。![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:new_window}
