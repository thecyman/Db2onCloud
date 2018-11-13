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

# 数据虚拟化（联合）
{: #overview}

{{site.data.keyword.Db2_on_Cloud_short}} 支持 Db2 数据虚拟化（也称为联合）。通过数据虚拟化，您能以单查询方式访问位于组织中任意位置的多个分布式数据库上的所有数据。"您可以访问位于任何 Db2 或 Informix 数据源（包括云和内部部署）上的数据。
{: shortdesc}

在所有版本的 {{site.data.keyword.Db2_on_Cloud_short}} 上都支持此功能，但免费的轻量套餐除外。但是，您可以使用轻量套餐作为可从中拉取数据的目标。

## 用例
{: #use_cases}

### 合并数据源

通过联合位于组织中任意位置的云和内部部署的数据源，如同从单个源检索虚拟化数据。数据虚拟化消除了繁重且耗费成本的数据迁移过程，使您能够高效且经济地分析所有数据。

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### 连接到 Db2 Warehouse on Cloud

Db2 系列产品的用户可联合 {{site.data.keyword.Db2_on_Cloud_short}} 和 {{site.data.keyword.dashdbshort_notm}} 数据库中的数据。从公共界面访问数据，您可以轻松添加、查询和分析数据而无需复杂的 ETL 过程和任何额外代码。

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### 在多台服务器之间分片数据

有时，您可能选择分区（分片）数据。利用联合功能，可使用统一界面查询分片的数据。联合使您能够更好地均衡工作负载、扩展应用程序的特定部分，以及创建协同工作的微服务。 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### 将数据库容量提高到超出固定限制

联合使您能够通过联合云上的数据库来提高内部部署数据库的容量。在内部部署数据库即将用尽存储容量时，此案例中的数据虚拟化是一个很好的选项。利用联合提高数据库容量适用于新开发，因为开发者无需更改已在生产中的数据库。您还可以联合两个 {{site.data.keyword.Db2_on_Cloud_short}} 数据库，以将数据库容量提高到超出 Flex 套餐的当前限制。

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## 入门
{: #getting_started}

以下步骤是如何联合不同的数据源以便看起来如同从单个源检索数据的示例。以下示例说明两个 {{site.data.keyword.Db2_on_Cloud_short}} 数据库的联合：

### 在 Db2 on Cloud 目标机器上

主机名：targetdotcom

1. 在模式 `admin2` 中创建表 `testdata`。

2. 在 {{site.data.keyword.Db2_on_Cloud_short}} 控制台中，使用用户 `admin2` 和密码 `YYYY` 将数据装入 `testdata` 表。

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

### 在将用作联合源的 Db2 on Cloud 机器上

在 {{site.data.keyword.Db2_on_Cloud_short}} 控制台中：

1. 创建服务器以与目标机器进行对话：<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   例如：<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. 针对 admin2 创建用户映射：<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   例如：<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. 为数据库创建昵称：<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   例如：<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. 测试是否可从目标服务器拉取数据：<br/>
   `select * from <nickname>`

   例如：<br/>
   `select * from ntest1`

## 其他信息

有关数据虚拟化（联合）的更多信息，请参阅：[联合 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}。

缺省情况下，{{site.data.keyword.Db2_on_Cloud_short}} 支持 Informix 和 Db2（包括内部部署 Db2 和 Db2 Warehouse）。可能需要根据请求由 IBM 支持人员安装对特定数据源的支持。有关联合支持的数据源的信息，请参阅：[联合支持的数据源 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}。

