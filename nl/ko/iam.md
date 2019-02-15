---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-21"

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

# IBM Cloud의 IAM(Identity and Access Management)
{: #iam}

IAM(Identity and Access Management)을 사용하면 플랫폼 서비스에 대해 사용자를 안전하게 인증하고 {{site.data.keyword.Bluemix_notm}} 플랫폼에서 일관되게 리소스에 대한 액세스를 제어할 수 있습니다. 예를 들어 IBM ID로 {{site.data.keyword.Bluemix_notm}}에 한 번만 로그인하면, 각각에 로그인할 필요 없이 모든 서비스 콘솔 및 애플리케이션에 액세스할 수 있습니다.
{: shortdesc}

## 인스턴스에서 IAM을 사용하도록 설정되어 있습니까?
{: #enabled}

일정 기간 동안 {{site.data.keyword.Bluemix_notm}}의 {{site.data.keyword.Db2_on_Cloud_long}} 관리 데이터베이스 인스턴스를 사용하여 IAM을 액세스 제어에 사용할 수 있습니다. 인스턴스에서 IAM이 사용으로 설정되어 있는지 확인하려면 다음 조회를 실행하십시오.

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

**IAM_ENABLED**의 리턴값이 1인 경우 인스턴스에서 IAM이 사용으로 설정됩니다.

## IBM Cloud IAM의 기능
{: #features}

두 가지 유형의 지원되는 ID로 {{site.data.keyword.Db2_on_Cloud_short}} 관리 서비스에 대해 다음 IAM 기능이 구현됩니다.

**IBM ID**

IBM ID가 있는 사용자를 특정 데이터베이스 서비스 인스턴스에 연결하려면 먼저 데이터베이스 관리자가 콘솔 또는 REST API를 통해 해당 사용자를 각 데이터베이스 서비스 인스턴스에 추가해야 합니다. 비IBM ID 사용자의 경우와 같이 IBM ID 사용자가 추가될 때 데이터베이스 서비스 인스턴스의 사용자 ID를 입력해야 합니다. 이 사용자 ID는 데이터베이스 서비스 인스턴스 내에서 고유해야 합니다. 또한 이 사용자 ID는 데이터베이스 내에서 권한 부여(AUTH) ID입니다. 데이터베이스 관리자는 AUTH ID를 기반으로 하여 권한을 부여하고 취소할 수 있습니다.

**서비스 ID**

서비스 ID는 사용자 ID가 사용자를 식별하는 방법과 유사하게 서비스 또는 애플리케이션을 식별합니다. 서비스 ID는 애플리케이션이 IBM Cloud 서비스로 인증하는 데 사용할 수 있는 ID입니다. 서비스 ID는 소유한 IBM ID와 별개의 항목입니다. 따라서 데이터베이스 내의 특정한 서비스 ID에 다른 권한을 부여할 수 있습니다. 서비스 ID에는 비밀번호가 없습니다. 데이터베이스 서비스 인스턴스에 연결할 각각의 서비스 ID에 대해 API 키를 작성해야 합니다. 서비스 ID에 대한 자세한 정보는 [IBM Cloud IAM 서비스 ID 및 API 키 소개 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}를 참조하십시오.

## 클라이언트 연결 및 사용자 로그인
{: #connect}

**필수 소프트웨어**: Db2 Client V11.1 FP3 이상.

다음은 IAM 인증을 위해 사용할 수 있는 방법입니다.

**액세스 토큰**

REST API를 통해 API 키를 사용하여 애플리케이션이 IAM 서비스에서 직접 액세스 토큰을 얻을 수 있습니다. 자세한 정보는 [API 키를 사용하여 IBM Cloud IAM 토큰 가져오기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}를 참조하십시오. 액세스 토큰의 기본 유효 기간은 만료되기 전 60분입니다. 토큰이 만료되면 Db2 서버에서 연결을 설정할 수 없습니다. 연결이 설정된 후에는 토큰 만료를 확인하지 않습니다. IAM 통합 이전과 같이 연결은 애플리케이션 연결이 끊어지거나 다른 이유로 인해 연결이 종료되기 전까지는 계속 연결되어 있습니다.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

액세스 토큰은 데이터베이스에 대한 IBM ID 사용자 또는 서비스 ID를 식별합니다. 데이터베이스 서버는 액세스 토큰을 승인하기 전에 액세스 토큰의 유효성을 확인합니다. 이 방법은 액세스 토큰을 유효성 검증하기 위해 IAM과 통신하는 과정을 최소화하므로 애플리케이션을 둘 이상의 데이터베이스 서비스 인스턴스 또는 다른 {{site.data.keyword.Bluemix_notm}} 서비스 인스턴스에 연결해야 하는 경우 가장 좋은 방법입니다.

**API 키**

각 IBM ID 사용자 또는 서비스 ID에 대해 여러 개의 API 키를 작성할 수 있습니다. 각 API 키는 일반적으로 단일 애플리케이션에 대해 작성됩니다. 소유한 IBM ID 또는 서비스 ID가 동일한 데이터베이스 서비스 인스턴스에 사용자로 추가되어 있는 한 애플리케이션을 데이터베이스 서비스 인스턴스에 연결할 수 있습니다. API 키는 데이터베이스 내에서 소유한 IBM ID 또는 서비스 ID와 동일한 권한을 가집니다. 애플리케이션을 더 이상 데이터베이스에 연결하지 않는 경우 해당 API 키를 제거할 수 있습니다. 이 인증 방법은 IAM 서비스와 직접 상호작용할 필요가 없으므로 액세스 토큰을 사용하는 경우보다 애플리케이션을 덜 변경합니다. API 키 작성 및 관리에 대한 자세한 정보는 [사용자 API 키 관리 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}를 참조하십시오.

**IBM ID/비밀번호**

IBM ID/비밀번호는 콘솔에 로그인하는 데 사용할 수 있으며 사용자 ID/비밀번호가 허용되는 것과 동일한 방식으로 애플리케이션 내에서 사용할 수도 있습니다. 조직의 로그인 페이지에 대한 리디렉션을 수행할 수 없기 때문에 IBM ID가 연합된 경우 예외가 발생합니다. 그러나 애플리케이션의 데이터베이스 서비스에 대한 연결을 설정하기 위해서는 액세스 토큰을 사용할 것을 권장합니다.

## 지원되는 인터페이스
{: #sup-if}

다음 데이터베이스 클라이언트 인터페이스가 지원됩니다.

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC, CLP 및 CLPPLUS
{: #odbc-clpplus}

IAM 인증을 사용하여 ODBC 애플리케이션 또는 명령행 클라이언트(CLP, CLPPLUS)를 Db2 서버에 연결하는 경우 먼저 다음 명령을 실행하여 `db2dsdriver.cfg` 구성 파일에 데이터 소스 이름(DSN)을 구성해야 합니다.

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

`db2dsdriver.cfg` 구성 파일은 일반적으로 `sqllib/cfg` 디렉토리에 있는 XML 파일이며, DSN 별명 목록과 해당 특성이 포함되어 있습니다.

다음은 데이터베이스 서비스 인스턴스에 대한 연결을 설정하는 데 사용되는 구성을 보여주는 `db2dsdriver.cfg` 구성 파일의 예입니다. 구성 파일은 DSN 별명, 데이터베이스 이름, 호스트 이름(또는 IP 주소) 및 **인증** 유형과 **SecurityTransportMode** 매개변수값을 제공합니다.

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<configuration>
        <dsncollection>
        <dsn alias="<data_source_name>" name="bludb" host="<host_name_or_IP_address>" port="50001">
            <parameter name="Authentication" value="GSSPLUGIN"/>
            <parameter name="SecurityTransportMode" value="SSL"/>
        </dsn>
        </dsncollection>
        <databases>
            <database name="bludb" host="<host_name_or_IP_address>" port="50001"/>
        </databases>
</configuration>
```

* ODBC 연결 문자열에는 다음 중 하나가 포함될 수 있습니다.

    **액세스 토큰**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **API 키**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBM ID/비밀번호**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    ODBC의 경우 **AUTHENTICATION=GSSPLUGIN**을 `db2dsdriver.cfg` 구성 파일 또는 애플리케이션의 연결 문자열에 지정할 수 있습니다.

* CLP CONNECT 명령문에는 다음 중 하나가 포함될 수 있습니다.

    **액세스 토큰**

    데이터베이스 서버 `<database_server_name>`에 연결하고 CLP 명령 프롬프트나 스크립트에서 다음 명령을 실행하여 액세스 토큰을 전달하십시오.

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **API 키**

    CLP 명령 프롬프트나 스크립트에서 다음 명령을 실행하여 API 키로 데이터베이스 서버 `<database_server_name>`에 연결하십시오.

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBM ID/비밀번호**

    CLP 명령 프롬프트나 스크립트에서 다음 명령을 실행하여 IBM ID/비밀번호로 데이터베이스 서버 `<database_server_name>`에 연결하십시오.

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    CLP로 데이터베이스 서버에 연결하는 데 관한 자세한 정보는 [CONNECT(유형 2) 명령문 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}을 참조하십시오. 

* CLPPLUS CONNECT 명령문에는 다음 중 하나가 포함될 수 있습니다.

    **액세스 토큰**

    CLPPLUS 명령 프롬프트 또는 스크립트에서 다음 명령을 실행하여 DSN 별명(`@<data_source_name>`)에 연결하고 액세스 토큰을 전달합니다.

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **API 키**

    CLPPLUS 명령 프롬프트 또는 스크립트에서 다음 명령을 실행하여 DSN 별명(`@<data_source_name>`)에 연결합니다.

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBM ID/비밀번호**

    CLPPLUS 명령 프롬프트 또는 스크립트에서 다음 명령을 실행하여 DSN 별명(`@<data_source_name>`)에 연결합니다.

    `connect <IBMid>/<password>@<data_source_name>`

    CLPPLUS를 사용하여 DSN 별명에 연결하는 데 대한 세부사항은 [CLPPlus의 DSN 별명 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}을 참조하십시오.

### JDBC
{: #jdbc}

IAM 인증에는 유형 4 JDBC 드라이버가 지원됩니다.

다음은 세 가지 방법에 대한 연결 스니펫을 보여주는 예입니다.

**액세스 토큰**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setAccessToken( "<access_token>" );
Connection conn = dataSource.getConnection( );
```

or

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**API 키**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setApiKey( "<api_key>" );
Connection conn = dataSource.getConnection( );
```

or

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apikey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBM ID/비밀번호**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<IBMid>", "<password>" );
```

or

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## 콘솔 사용자 환경
{: #console-ux}

서비스 콘솔 로그인 페이지에는 IBM ID 및 비밀번호를 사용하여 로그인하는 옵션이 있습니다. **IBM ID를 통해 로그인** 단추를 클릭하면 사용자는 비밀번호가 입력되는 IAM 로그인 페이지로 이동합니다. 인증이 완료되면 사용자가 다시 콘솔로 리디렉션됩니다. 이러한 로그인이 성공하려면 먼저 데이터베이스 관리자가 콘솔 또는 REST API를 통해 IBM ID 사용자를 각 데이터베이스 서비스 인스턴스에 추가해야 합니다. 비IBM ID 사용자의 경우와 같이 IBM ID 사용자가 추가될 때 데이터베이스 서비스 인스턴스의 사용자 ID를 입력해야 합니다. 사용자 ID는 데이터베이스 서비스 인스턴스 내에서 고유해야 합니다. 또한 이 사용자 ID는 데이터베이스 내에서 권한 부여(AUTH) ID입니다.

## REST API 환경
{: #api}

{{site.data.keyword.Db2_on_Cloud_short}} REST API는 이전에 데이터베이스 서비스 생성 액세스 토큰을 허용한 기능에 대해 IAM 액세스 토큰도 허용하도록 향상되었습니다.

* 새 IBM ID 사용자를 추가하려면 다음 API 호출 예제를 실행하십시오.

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  `"id"` 및 `"ibmid"`의 `<userid>` 값은 같을 필요가 없습니다. 두 개의 다른 ID는 어떠한 방법으로도 함께 링크되지 않습니다.
  {: note}

* 기존 비IBM ID 데이터베이스 사용자(예: `abcuser`)를 마이그레이션하여 IBM ID 사용자로 만들려면 먼저 다음 API 호출 예제를 실행하여 비IBM ID 사용자 ID를 삭제하십시오.

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  다음 API 호출 예제를 실행하여 이전 사용자 ID(`abcuser`)와 동일한 IBM ID로 사용자를 다시 추가하십시오.

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  사용자 ID(`abcuser`)는 해당 사용자의 새 IBM ID에 대해 동일하게 유지되므로 사용자에 대해 허용된 데이터베이스 권한은 변경되지 않고 그대로 유지됩니다. IBM ID 사용자로 만들기 위해 기존 비 IBM ID 데이터베이스 사용자 목록을 마이그레이션해야 하는 경우 각 사용자에 대한 이전 API 호출 쌍을 실행해야 합니다.

* 다수의 새 IBM ID 사용자를 한 번에 추가하려면 각 사용자에 대해 하나씩 다음 API 호출 예제를 나열하는 일괄처리 파일을 작성하십시오.

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

서비스 API에 대한 세부사항은 [{{site.data.keyword.Db2_on_Cloud_short}} REST API ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://ibm.biz/db2oc_api){:new_window}를 참조하십시오.

## IBM ID 연합
{: #fed}

LDAP과 같은 사용자 고유의 ID 제공자를 사용하려면 먼저 LDAP 서버를 IBM ID와 연합해야 합니다. LDAP 서버를 IBM ID와 연합하는 데 대한 지시사항은 [IBM ID 엔터프라이즈 연합 채택 안내서 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}를 참조하십시오. IBM ID 연합이 완료되고 데이터베이스 관리자가 허용된 사용자를 데이터베이스 서비스 인스턴스에 추가하면 해당 사용자가 회사 사용자 ID 및 비밀번호를 사용하여 콘솔에 로그인할 수 있습니다. 또는 해당 사용자는 사용자 ID를 나타내는 액세스 토큰 또는 API 키를 사용하여 지원되는 데이터베이스 클라이언트 인터페이스 중 하나를 통해 데이터베이스 서비스 인스턴스에 연결할 수 있습니다.

## 제한사항
{: #restrictions}

다음은 IAM 인증과 관련된 제한사항입니다.

* Db2 서버에 연결되는 Db2 클라이언트에 대한 IAM 인증은 SSL 연결을 통해서만 지원됩니다.
* IBM ID 연합은 사용자 정의 사용자 관리 포털 또는 서버를 인증에 사용하기 위해 지원됩니다. 그룹 연합은 이러한 지원에 포함되지 않습니다.
* 데이터베이스 연합에 대한 IAM 인증은 지원되지 않습니다.
* CLPPlus를 통한 IDA 및 사용자 정의 확장(UDX) 명령 실행은 지원되지 않습니다.
* 유형 2 JDBC 드라이버는 지원되지 않습니다.




