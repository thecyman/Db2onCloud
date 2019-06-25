---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-30"

keywords: 

subcollection: Db2onCloud

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
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 시작하기 튜토리얼
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}}는 클라우드에서 사용자를 위해 프로비저닝된 SQL 데이터베이스입니다. {{site.data.keyword.Db2_on_Cloud_short}}는 다른 데이터베이스 소프트웨어를 사용하는 것과 동일하게 사용할 수 있지만, 하드웨어 설정이나 소프트웨어 설치 및 관리에 소요되는 시간 및 비용이 없습니다.
{: shortdesc}

인증 정보를 작성하십시오. IBM Cloud를 처음 사용하는 경우 서비스를 작성한 다음 서비스를 시작할 때 **인증 정보 작성** 단추를 클릭하여 사용자 이름과 비밀번호를 작성해야 합니다. 엄밀히 말하면 인증 정보 없이도 웹 콘솔에 로그인할 수 있지만, 대부분의 Db2 도구를 사용하려면 사용자 이름과 비밀번호가 필요합니다.
{: important}

[무료 Db2 Developer Edition 다운로드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:new_window}를 사용하여 로컬 Db2 데이터베이스를 설치할 수도 있습니다. 이는 Docker 컨테이너 내에 도구를 포함하는 즉시 사용 가능한 Db2 개발자 에디션을 빠르게 설치합니다(Docker는 필요하지 않으며 필요한 컴포넌트는 자동으로 설치됨).  

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

### 컴퓨터에 Db2 명령행 클라이언트 및 드라이버 설치
{: #connect_apps}

대부분의 경우 사용자는 REST API만 사용하거나 프레임워크의 드라이버를 설치합니다(예: Python의 `pip` 명령 사용).
{: shortdesc}

MacOS용 Python 드라이버 패키지를 설치하려면 `pip` 명령을 `--no-cache-dir` 옵션과 함께 사용해야 합니다. 자세한 지시사항은 [Python support for IBM DB2 and IBM Informix ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2-drivers-python){:new_window}를 참조하십시오.
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

Python 또는 Node.js 프레임워크 드라이버를 설치하려면 다음 링크 중 하나를 클릭하십시오. 
- [Python 드라이버 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2-drivers-python){:new_window}
- [Node.js 드라이버 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2-drivers-node){:new_window}

Sequelize라는 Node.js ORM을 설치하려면 다음 링크를 클릭하십시오.
[Sequelize ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibmdb/sequelize){:new_window}
{: note}

Java, Go, Jupyter Notebooks, Ruby, PHP 등을 포함하는 추가 드라이버 설치 옵션은 다음 링크를 클릭하십시오.  

- [ibmdb ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibmdb){:new_window}

프레임워크 드라이버를 이미 설치한 경우에는 다음 단계를 건너뛸 수 있습니다. 그러나 파워유저는 Db2 명령행 클라이언트를 사용하여 데이터베이스를 관리하고 Db2 명령을 사용하려 할 수 있습니다. 특정 ODBC 또는 JDBC 연결에서 일반 Db2 드라이버 설치도 이용할 수 있습니다. 이 경우 다음 단계를 완료하십시오.

1. 앱 또는 도구가 실행 중인 컴퓨터에서 [Install the driver package ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window}를 수행하십시오.
2. {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 대해 [Configure the driver files ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}를 수행하십시오.

### {{site.data.keyword.Bluemix_notm}} 앱 또는 서비스의 데이터 소스로 Db2 on Cloud 사용
{: #data_src}

{{site.data.keyword.Bluemix_notm}}에서 호스팅되는 앱은 로컬 애플리케이션이 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 연결하는 것과 동일한 방식으로 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에 연결할 수 있습니다.
{: shortdesc}

앱이 {{site.data.keyword.Bluemix_notm}} 플랫폼을 사용할 때 `VCAP _SERVICES` 환경 변수를 이용하여 데이터베이스 세부사항 및 인증 정보를 지정하는 태스크를 단순화할 수 있습니다.
1. {{site.data.keyword.Bluemix_notm}} 대시보드에 있는 {{site.data.keyword.Db2_on_Cloud_long_notm}} 서비스를 위한 서비스 세부사항 페이지의 **연결** 탭에서 **연결 작성** 단추를 클릭하십시오.
2. 데이터 소스로서 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스와 함께 사용할 {{site.data.keyword.Bluemix_notm}} 앱을 선택한 후에 **연결** 단추를 클릭하십시오.
3. 애플리케이션 코드를 업데이트하여 `VCAP_SERVICES` 환경 변수에서 데이터베이스 세부사항 및 인증 정보를 검색하십시오.

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
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window} -->

## 동영상: Db2 on Cloud 소개
{: #intro_vid}

{{site.data.keyword.Db2_on_Cloud_short}}에 대한 소개를 보려면 이 동영상을 시청하십시오.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="소개 - {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## 동영상: REST API를 사용하여 Db2 on Cloud와 통신
{: #vid_api}

RESTful API를 사용하여 {{site.data.keyword.Db2_on_Cloud_short}}와 통신하는 데 필요한 단계를 보려면 이 동영상을 시청하십시오.

<iframe class="embed-responsive-item" id="youtubeplayer2" title="RESTful API를 사용하여 {{site.data.keyword.Db2_on_Cloud_short}}와 통신" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## 동영상: Jupyter Notebook 통합
{: #cognos_vid}

Jupyter Notebook을 {{site.data.keyword.Db2_on_Cloud_short}}와 통합하는 방법을 보려면 이 동영상을 시청하십시오. 

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Jupyter Notebook 통합" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


