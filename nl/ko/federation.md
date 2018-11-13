---

copyright:
  years: 2014, 2018
lastupdated: "2018-10-26"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# 데이터 가상화(연합)
{: #overview}

Db2 데이터 가상화(연합이라고도 함)는 {{site.data.keyword.Db2_on_Cloud_short}}에서 지원됩니다. 데이터 가상화를 사용하면 조직 내 어느 위치에서든 다중 분산 데이터베이스에 있는 모든 데이터에 대한 단일 조회 액세스가 가능합니다. 온프레미스 및 클라우드에서 Db2 또는 Informix 데이터 소스에 있는 데이터에 액세스할 수 있습니다. 
{: shortdesc}

이 기능은 무료 라이트 플랜을 제외한 모든 버전의 {{site.data.keyword.Db2_on_Cloud_short}}에 지원됩니다. 하지만 데이터를 가져올 수 있는 대상으로 라이트 플랜을 사용할 수 있습니다.

## 유스 케이스
{: #use_cases}

### 데이터 소스 통합

조직의 어느 위치에서든 온프레미스 및 클라우드에 있는 데이터 소스를 연합하면 가상화된 데이터가 단일 소스에서 검색되는 것으로 보입니다. 데이터 가상화를 사용하면 까다로우며 비용이 드는 데이터 마이그레이션 프로세스가 사라져 효과적이며 비용 효율적으로 모든 데이터를 분석할 수 있습니다.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Db2 Warehouse on Cloud에 연결

Db2 제품군의 제품 사용자는 {{site.data.keyword.Db2_on_Cloud_short}} 및 {{site.data.keyword.dashdbshort_notm}} 데이터베이스의 데이터를 연합할 수 있습니다. 데이터에 액세스하는 데 필요한 공통 인터페이스를 사용하여 복잡한 ETL 프로세스 없이 그리고 추가 코드 없이 데이터를 쉽게 추가하고 조회하고 분석할 수 있습니다.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### 다중 서버의 샤드된 데이터

때로는 데이터를 파티셔닝(샤드)하도록 선택할 수 있습니다. 연합 기능을 사용하면 통합 인터페이스를 통해 샤드된 데이터를 조회할 수 있습니다. 연합을 사용하면 보다 효율적으로 워크로드를 밸런싱하고 앱의 특정 파트를 스케일링하며 함께 작동되는 마이크로서비스를 작성할 수 있습니다. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### 고정된 한계를 초과하여 데이터베이스 용량 증가

연합을 사용하면 클라우드의 데이터베이스와 연합하여 온프레미스 데이터베이스의 용량을 늘릴 수 있습니다. 이 경우의 데이터 가상화는 온프레미스 데이터베이스의 용량이 부족한 경우에 훌륭한 옵션입니다. 개발자가 프로덕션에서 아직 데이터베이스를 변경할 필요가 없으므로 연합을 통한 데이터베이스 용량 증가는 새 개발의 경우에 유용합니다. 또한 두 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스를 연합하여 Flex 플랜의 현재 한계를 초과하도록 데이터베이스 용량을 늘릴 수 있습니다.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## 시작하기
{: #getting_started}

다음 단계는 서로 다른 데이터 소스를 연합하여 단일 소스에서 데이터가 검색되는 것처럼 보이게 하는 방법의 예입니다. 다음 예는 두 개의 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스의 연합을 보여줍니다.

### Db2 on Cloud 대상 시스템의 경우

호스트 이름: targetdotcom

1. `admin2` 스키마에서 `testdata` 테이블을 작성하십시오.

2. {{site.data.keyword.Db2_on_Cloud_short}} 콘솔에서 사용자 `admin2` 및 비밀번호 `YYYY`를 사용하여 데이터가 포함된 `testdata` 테이블을 로드하십시오.

<!-- ### On a client machine of the target

1. Catalog the target machine:<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   For example:<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. Catalog the database on fedS:<br/>
   `db2 catalog db bludb as <db_name> at node <node_name>`

   For example:<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. Connect to the database on fedS:<br/>
   `db2 connect to <catalog_db_name> user <admin_user> using '<admin_password>'`

   For example:<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. Create a wrapper on fedS:<br/>
   `db2 "create wrapper drda"`

5. Create a server to talk to the target machine:<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   For example:<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. Create the user mapping for admin2:<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   For example:<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. Create a nickname for the database:<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   For example:<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### On the Db2 on Cloud source machine

1. Test that you can pull data from the target server:<br/>
   `db2 "select * from <nickname>"`

   For example:<br/>
   `db2 "select * from ntest1"`
-->

### 연합 소스로 사용 중인 Db2 on Cloud 시스템의 경우

{{site.data.keyword.Db2_on_Cloud_short}} 콘솔에서 다음을 수행하십시오.

1. 대상 시스템과 대화하는 서버를 작성하십시오.<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   예를 들어, 다음과 같습니다.<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. admin2의 사용자 맵핑을 작성하십시오.<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   예를 들어, 다음과 같습니다.<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. 데이터베이스의 닉네임을 작성하십시오.<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   예를 들어, 다음과 같습니다.<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. 대상 서버에서 데이터를 가져올 수 있는지 테스트하십시오.<br/>
   `select * from <nickname>`

   예를 들어, 다음과 같습니다.<br/>
   `select * from ntest1`

## 추가 정보

데이터 가상화(연합)에 대한 자세한 정보는 [Federation![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}을 참조하십시오.

기본적으로 {{site.data.keyword.Db2_on_Cloud_short}}는 Informix 및 Db2(온프레미스 Db2 및 Db2 Warehouse 포함)를 지원합니다. 요청 시 IBM 지원 센터에서 특정 데이터 소스에 대한 지원을 설치해야 할 수 있습니다. 연합을 통해 지원되는 데이터 소스에 대한 정보는 [Federation Supported Data Sources![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}를 참조하십시오.

