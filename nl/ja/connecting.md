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

# 接続
{: #connect}

コマンド行インターフェース、IBM® またはサード・パーティーのアプリケーションやツール、作成したアプリケーションを Db2® データベースに接続できます。 
{: shortdesc}

## 前提条件
{: #connect_prereq}

接続で問題が生じる場合は、[前提条件 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:new_window}を満たすようにしてください。
{: shortdesc}

### 環境の構成
{: #cfg_env}

ローカル・アプリケーションやツールを Db2 データベースに接続するには、[環境の構成 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}を行う必要があります。 
{: shortdesc}

## プログラムによる接続
{: #conx_prgrm}

共通プログラミング言語を使用して、Db2 データベースに接続するアプリケーションを作成できます。
{: shortdesc}

<!--* [Java ![External link icon](../../icons/launch-glyph.svg "External link icon"){}{:new_window} -->
* [JDBC ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
* [ODBC ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:new_window}
* [.NET ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
* [PHP ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}

## アプリケーションとツールの接続
{: #conx_apps_tools}

また、外部アプリケーションやツールを {{site.data.keyword.Db2_on_Cloud_short}} に接続して利用し、
データをさらに管理または分析することも可能です。 例えば、以下を行えます。
   * 分析データベースを必要とする {{site.data.keyword.Bluemix_short}} アプリケーションを接続します。
   * [{{site.data.keyword.DSX_full}} (以前の IBM Data Science Experience) から接続します。 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:new_window}
   * [{{site.data.keyword.IBM_notm}} InfoSphere® Data Architect を接続して、データベース・スキーマを設計およびデプロイします。 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:new_window}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [{{site.data.keyword.IBM_notm}} Cognos® サーバーを接続して、データに対して Cognos レポートを実行します。 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:new_window}
   * SQL ベースのツール (Tableau、Microsoft Excel など) を接続して、データを操作、分析、または視覚化します。 
       * [Tableau ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:new_window}
       * [Microsoft Excel ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:new_window}
   * [Aginity Workbench を接続して、Netezza® データ・モデルおよびデータを {{site.data.keyword.dashdbshort_notm}} にマイグレーションします。 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:new_window}
