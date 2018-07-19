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

# 시작하기
{: #getting_started_db2oncloud}

{{site.data.keyword.Db2_on_Cloud_long}}는 클라우드에서 사용자를 위해 프로비저닝된 SQL 데이터베이스입니다. 데이터베이스 소프트웨어를 사용하는 것처럼 {{site.data.keyword.Db2_on_Cloud_short}}를 사용할 수 있지만 하드웨어 설정 또는 소프트웨어 설치 및 관리라는 번거로움을 덜 수 있습니다. 

북아메리카 대륙 밖에서 무료 라이트 플랜을 배치하는 경우 [북아메리카 대륙 밖에서 라이트 플랜 사용](free_plan.html#outside_na){:new_window}을 참조하십시오.
{: shortdesc}

[free Db2 Developer Edition download ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions)를 사용하여 로컬 Db2 데이터베이스도 설치할 수 있습니다. Docker 컨테이너 내부의 도구로, 바로 사용할 수 있는 Db2 개발자 에디션을 빠르게 설치합니다(Docker는 필요 없으며 필요한 컴포넌트는 자동으로 생성됨). 

<!-- ## Free trial
{: #freetrial}

You can try the {{site.data.keyword.Db2_on_Cloud_short}} Precise Performance 500 (2.8.500) plan for 7 days on {{site.data.keyword.Bluemix_notm}} without charge. [Free trial ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/db2){:new_window} -->

## 인터페이스
{: #interfaces}

다음과 같은 방법으로 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스 관련 작업을 수행할 수 있습니다.
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} 웹 콘솔
   * REST API
   * 로컬 컴퓨터에서 애플리케이션 또는 선호하는 도구 연결
   * {{site.data.keyword.Bluemix_notm}} 앱 또는 서비스의 데이터 소스로 {{site.data.keyword.Db2_on_Cloud_short}} 사용

### Db2 on Cloud 웹 콘솔
{: #web_console}

웹 콘솔은 데이터베이스를 사용하는 데에 필요한 모든 기능(로드 기능, SQL 편집기, 드라이버 다운로드 등)에 대한 그래픽 인터페이스를 제공합니다.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

다음과 같은 방법으로 {{site.data.keyword.Db2_on_Cloud_short}} 웹 콘솔에 액세스할 수 있습니다.
   * {{site.data.keyword.Bluemix_notm}} 대시보드를 통해 - {{site.data.keyword.Db2_on_Cloud_long_notm}} 서비스의 서비스 세부사항 페이지에서 웹 콘솔을 열 수 있습니다.
   * 직접 URL - {{site.data.keyword.Db2_on_Cloud_short}} 서비스의 웹 콘솔 URL에 책갈피를 지정할 수 있습니다.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

### 로컬 컴퓨터에서 애플리케이션 또는 선호하는 도구 연결
{: #connect_apps}

다음 단계를 완료하여 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 연결하도록 로컬 환경을 구성하십시오.
{: shortdesc}

1. {{site.data.keyword.Db2_on_Cloud_short}} 웹 콘솔의 연결 정보 페이지에서 [driver package ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window}를 다운로드하십시오.
2. 앱 또는 도구가 실행 중인 컴퓨터에서 [Install the driver package ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window}를 수행하십시오.
3. {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 대해 [Configure the driver files ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}를 수행하십시오.

### {{site.data.keyword.Bluemix_notm}} 앱 또는 서비스의 데이터 소스로 Db2 on Cloud 사용
{: #data_src}

{{site.data.keyword.Bluemix_notm}}에서 호스팅되는 앱은 로컬 애플리케이션이 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 연결하는 것과 정확히 동일한 방식으로 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 연결할 수 있습니다.
{: shortdesc}

앱이 {{site.data.keyword.Bluemix_notm}} 플랫폼을 사용할 때 `VCAP _SERVICES` 환경 변수를 이용하여 데이터베이스 세부사항 및 신임 정보를 지정하는 태스크를 단순화할 수 있습니다.
1. {{site.data.keyword.Bluemix_notm}} 대시보드에 있는 {{site.data.keyword.Db2_on_Cloud_long_notm}} 서비스를 위한 서비스 세부사항 페이지의 **연결** 탭에서 **연결 작성** 단추를 클릭하십시오.
2. 데이터 소스로서 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스와 함께 사용할 {{site.data.keyword.Bluemix_notm}} 앱을 선택한 후에 **연결** 단추를 클릭하십시오.
3. 애플리케이션 코드를 업데이트하여 `VCAP_SERVICES` 환경 변수에서 데이터베이스 세부사항 및 신임 정보를 검색하십시오.

    **`VCAP_SERVICES`가 없는 예제**

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

    **`VCAP_SERVICES`가 있는 예제**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## 샘플
{: #samples}

다음은 여러 언어로 된 애플리케이션에서 사용자의 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스로 연결하는 방법을 보여주는 샘플에 대한 링크입니다.
{: shortdesc}

   * [.NET ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
   * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window}


