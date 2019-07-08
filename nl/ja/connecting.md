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

# 接続
{: #connect}

コマンド行インターフェース、IBM® またはサード・パーティーのアプリケーションやツール、作成したアプリケーションを Db2® データベースに接続できます。 
{: shortdesc}

## 前提条件
{: #connect_prereq}

接続で問題が生じる場合は、[前提条件](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:external}を満たすようにしてください。
{: shortdesc}

### 環境の構成
{: #cfg_env}

ローカル・アプリケーションやツールを Db2 データベースに接続するには、[環境の構成](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external}が必要です。
{: shortdesc}

## プログラムによる接続
{: #conx_prgrm}

共通プログラミング言語を使用して、Db2 データベースに接続するアプリケーションを作成できます。
{: shortdesc}

<!--* [Java{}{:external} -->
* [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
* [ODBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:external}
* [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
* [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}

## アプリケーションとツールの接続
{: #conx_apps_tools}

また、外部アプリケーションやツールを {{site.data.keyword.Db2_on_Cloud_short}} に接続して利用し、
データをさらに管理または分析することも可能です。 例えば、以下を行えます。
   * 分析データベースを必要とする {{site.data.keyword.Bluemix_short}} アプリケーションを接続します。
   * [{{site.data.keyword.DSX_full}} (以前の IBM Data Science Experience) から接続します。](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:external}
   * [{{site.data.keyword.IBM_notm}}InfoSphere® Data Architect を接続して、データベース・スキーマを設計およびデプロイします。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:external}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [{{site.data.keyword.IBM_notm}}Cognos® サーバーを接続して、データに対して Cognos レポートを実行します。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:external}
   * SQL ベースのツール (Tableau、Microsoft Excel など) を接続して、データを操作、分析、または視覚化します。 
       * [Tableau](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:external}
       * [Microsoft Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:external}
   * [Aginity Workbench を接続して、Netezza® データ・モデルおよびデータを {{site.data.keyword.dashdbshort_notm}} にマイグレーションします。](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:external}
