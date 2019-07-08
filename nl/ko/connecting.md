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

# 연결
{: #connect}

명령행 인터페이스, IBM® 또는 서드파티 애플리케이션이나 도구, 작성한 앱을 Db2® 데이터베이스에 연결할 수 있습니다. 
{: shortdesc}

## 전제조건
{: #connect_prereq}

연결 중에 문제점이 발생하면 [전제조건](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:external}을 완료하십시오.
{: shortdesc}

### 환경 구성
{: #cfg_env}

로컬 애플리케이션 및 도구를 Db2 데이터베이스에 연결하려면 [환경 구성](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external}을 수행해야 합니다.
{: shortdesc}

## 프로그래밍 방식으로 연결
{: #conx_prgrm}

공통 프로그래밍 언어를 사용하여 Db2 데이터베이스에 연결하는 애플리케이션을 작성할 수 있습니다.
{: shortdesc}

<!--* [Java{}{:external} -->
* [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
* [ODBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:external}
* [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
* [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}

## 앱 및 도구 연결
{: #conx_apps_tools}

또한 외부 애플리케이션 및 도구를 {{site.data.keyword.Db2_on_Cloud_short}}에 연결하고 이를 사용하여 데이터를 관리하고 분석할 수 있습니다. 예를 들어, 다음과 같습니다.
   * 분석 데이터베이스가 필요한 {{site.data.keyword.Bluemix_short}} 애플리케이션을 연결합니다.
   * [{{site.data.keyword.DSX_full}}(이전의 IBM Data Science Experience)에서 연결합니다.](https://datascience.ibm.com/docs/content/manage-data/create-conn.html?context=analytics&linkInPage=true){:external}
   * [{{site.data.keyword.IBM_notm}} InfoSphere® Data Architect를 연결하여 데이터베이스 스키마를 디자인하고 배치합니다.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:external}
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
   * [{{site.data.keyword.IBM_notm}} Cognos® 서버를 연결하여 데이터에 대한 Cognos 보고서를 실행합니다.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:external}
   * Tableau 또는 Microsoft Excel과 같은 SQL 기반 도구를 연결하여 데이터를 조작하거나 분석하거나 시각화합니다. 
       * [Tableau](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:external}
       * [Microsoft Excel](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:external}
   * [Aginity Workbench를 연결하여 Netezza® 데이터 모델 및 데이터를 {{site.data.keyword.dashdbshort_notm}}로 마이그레이션합니다.](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:external}
