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

# 연결
{: #connect}

명령행 인터페이스, IBM® 또는 서드파티 애플리케이션이나 도구, 작성한 앱을 Db2® 데이터베이스에 연결할 수 있습니다. 
{: shortdesc}

## 전제조건
{: #connect_prereq}

연결 중에 문제점이 발생하면 [전제조건 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:new_window}을 완료하십시오.
{: shortdesc}

### 환경 구성
{: #cfg_env}

Db2 데이터베이스에 로컬 애플리케이션 및 도구를 연결하려면 [환경 구성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}을 수행해야 합니다. 
{: shortdesc}

## 프로그래밍 방식으로 연결
{: #conx_prgrm}

공통 프로그래밍 언어를 사용하여 Db2 데이터베이스에 연결하는 애플리케이션을 작성할 수 있습니다.
{: shortdesc}

<!--* [Java ![External link icon](../../icons/launch-glyph.svg "External link icon"){}{:new_window} -->
* [JDBC ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
* [ODBC ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:new_window}
* [.NET ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
* [PHP ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}

## 앱 및 도구 연결
{: #conx_apps_tools}

또한 외부 애플리케이션 및 도구를 {{site.data.keyword.Db2_on_Cloud_short}}에 연결하고 이를 사용하여 데이터를 관리하고 분석할 수 있습니다. 예를 들어, 다음과 같습니다.
   * 분석 데이터베이스가 필요한 {{site.data.keyword.Bluemix_short}} 애플리케이션을 연결합니다.
   * [{{site.data.keyword.DSX_full}}(이전 이름:IBM Data Science Experience)에서 연결합니다. ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:new_window}
   * [{{site.data.keyword.IBM_notm}} InfoSphere® Data Architect를 연결하여 데이터베이스 스키마를 디자인하고 배치합니다. ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:new_window}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [{{site.data.keyword.IBM_notm}} Cognos® 서버를 연결하여 데이터에 대한 Cognos 보고서를 실행합니다. ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:new_window}
   * Tableau 또는 Microsoft Excel과 같은 SQL 기반 도구를 연결하여 데이터를 조작하거나 분석하거나 시각화합니다. 
       * [Tableau ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:new_window}
       * [Microsoft Excel ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:new_window}
   * [Aginity Workbench를 연결하여 Netezza® 데이터 모델 및 데이터를 {{site.data.keyword.dashdbshort_notm}}에 마이그레이션합니다. ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:new_window}
