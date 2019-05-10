---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-26"

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

# データ仮想化 (フェデレーション)
{: #fed}

Db2 データ仮想化 (フェデレーション) は {{site.data.keyword.Db2_on_Cloud_short}} でサポートされています。 データ仮想化によって、組織内の任意の場所にある複数の分散データベース上にあるすべてのデータに対して単一照会アクセスが可能になります。 クラウドとオンプレミスの両方の Db2 または Informix のデータ・ソースにあるデータにアクセスできます。 
{: shortdesc}

このファンクションは、無料のライト・プランを除き、{{site.data.keyword.Db2_on_Cloud_short}} のすべてのバージョンでサポートされています。 ただし、Lite プランをデータ取得の
ターゲットとして使用することは可能です。

## ユース・ケース
{: #use_cases}

### データ・ソースの統合

クラウドに配置されたデータと組織のオンプレミス・データをフェデレートすることで、仮想化データは単一のソースから取得されているように見えます。 データ仮想化によって、煩雑でコストのかかるデータ・マイグレーションの作業
が軽減され、ユーザーは高い効率と費用効果ですべてのデータを分析することが可能になります。

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Db2 Warehouse on Cloud への接続

Db2 ファミリー製品のユーザーは、
{{site.data.keyword.Db2_on_Cloud_short}} および
{{site.data.keyword.dashdbshort_notm}} データベースのデータを統合できます。 一般的なインター
フェースを使用してデータにアクセスしてデータを簡単に追加、照会、および分析することができ、複
雑な ETL プロセスや追
加コードは必要ありません。

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### 複数サーバーでのデータ・シャード

ときには、ユーザーがデータを分割（シャード）していることもあります。 フェデレーション機能を使用すると、統一されたインターフェ
ースでシャード・データを照会することができます。 フェデレーションによって、作業負荷をバランスよく配分したり、アプリケーションの特定部
分を拡張したり、適切に連携するマイクロサービスを確立したりすることができます。 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### 制限を超えたデータベース容量の拡張

フェデレーションでは、クラウド上のデータベースと連携することにより、オンプレミス・
データベースの容量を増やすことができます。 このケースにおけるデータ仮想化は、オンプレミス・データベースのストレージが不足し
ている
場合に最適です。 フェデレーションによるデータベース容量の拡張は、新規開発にも役立ちます。なぜな
ら、開発者は本番環境のデータベースを変更する必要がないからです。 2 つの {{site.data.keyword.Db2_on_Cloud_short}} デ
ータベースを統合すると、Flex プランの現在の制限を超えてデータベースの容量を増やすこともで
きます。

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## 概説
{: #getting_started_fed}

以下の手順では、分散したデータ・ソースを統合し、あたかも 1 つのデータ・ソースからデー
タを取得しているように見せる方法を例示します。 2 つの
{{site.data.keyword.Db2_on_Cloud_short}} データベースをフェデレーションする例を以下に示し
ます。

### Db2 on Cloud ターゲット・マシン上:
{: #targ}

ホスト名: targetdotcom

1. スキーマ `admin2` にテーブル `testdata` を作成します。

2. ユーザー `admin2` として、パスワード `YYYY` を使用して、{{site.data.keyword.Db2_on_Cloud_short}} コンソールからデータが入った `testdata` テーブルをロードします。

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

### フェデレーション・ソースとして使用されている Db2 on Cloud マシン上:
{: #fed_src}

{{site.data.keyword.Db2_on_Cloud_short}} コンソールから、以下を行います。

1. ターゲット・マシンと通信するサーバーを作成します。<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   例えば、以下のようにします。<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. admin2 のユーザー・マッピングを作成します。<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   例えば、以下のようにします。<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. データベースのニックネームを作成します。<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   例えば、以下のようにします。<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. ターゲット・サーバーからデータを取得できることをテストします。<br/>
   `select * from <nickname>`

   例えば、以下のようにします。<br/>
   `select * from ntest1`

## 追加情報
{: #more_info}

データ仮想化 (フェデレーション) について詳しくは、[フェデレーション ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window} を参照してください。


デフォルトでは、{{site.data.keyword.Db2_on_Cloud_short}} は Informix および Db2 (オンプレミス Db2 および Db2 Warehouse を含む) をサポートします。 特定のデータ・ソースのサポートを IBM サポートが要求に応じてインストールしなければならない場合があります。 フェデレーションでサポートされるデータ・ソースについて詳しくは、
[フェデレーションでサポートされるデータ・ソース ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window} を参照してください。

