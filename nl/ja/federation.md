---

copyright:
  years: 2014, 2018
lastupdated: "2018-06-15"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# データ仮想化 (フェデレーション)
{: #overview}

Db2 データ仮想化 (フェデレーション) は
{{site.data.keyword.Db2_on_Cloud_short}} でサポートされています。データを仮想化することで、社内にある
複数
の分散データベースに配置されたすべてのデータに 1 回のクエリーでアクセスすることができます。
ユーザーは、クラウドとオンプレミスの両方に配置された Db2 または Informix データ・ソースにアク
セスでき
ます。{: shortdesc}

この機能は、無料の Lite プランを除く {{site.data.keyword.Db2_on_Cloud_short}} の全バ
ージョンでサポートされます。ただし、Lite プランをデータ取得の
ターゲットとして使用することは可能です。

## ユース・ケース
{: #use_cases}

### データ・ソースの統合

クラウドに配置されたデータと社内のオンプレミス・データをフェデレートすることで、
仮想化データは単一のソースから取得されているように見えます。データ仮想化によって、煩雑でコストのかかるデータ・マイグレーションの作業
が軽
減され、ユーザーは高い効率と費用効果ですべてのデータを分析することが可能になります。

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### クラウド上の Db2 Warehouse への接続

Db2 ファミリー製品のユーザーは、
{{site.data.keyword.Db2_on_Cloud_short}} および
{{site.data.keyword.dashdbshort_notm}} データベースのデータを統合できます。一般的なインター
フェースを使用してデータにアクセスしてデータを簡単に追加、照会、および分析することができ、複
雑な ETL プロセスや追
加コードは必要ありません。

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### 複数サーバーでのデータ・シャード

ときには、ユーザーがデータを分割（シャード）していることもあります。フェデレーション機能を使用すると、統一されたインターフェ
ースでシャード・データを照会することができます。フェデレーションによって、作業負荷をバランスよく配分したり、アプリケーションの特定部
分を拡張したり、適切に連携するマイクロサービスを確立したりすることができます。 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### 制限を超えたデータベース容量の拡張

フェデレーションでは、クラウド上のデータベースと連携することにより、オンプレミス・
データベースの容量を増やすことができます。このケースにおけるデータ仮想化は、オンプレミス・データベースのストレージが不足し
ている
場合に最適です。フェデレーションによるデータベース容量の拡張は、新規開発にも役立ちます。なぜな
ら、開発者は本番環境のデータベースを変更する必要がないからです。2 つの {{site.data.keyword.Db2_on_Cloud_short}} デ
ータベースを統合すると、Flex プランの現在の制限を超えてデータベースの容量を増やすこともで
きます。

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## 概説
{: #getting_started}

以下の手順では、分散したデータ・ソースを統合し、あたかも 1 つのデータ・ソースからデー
タを取得しているように見せる方法を例示します。2 つの
{{site.data.keyword.Db2_on_Cloud_short}} データベースをフェデレーションする例を以下に示し
ます。

### クラウド ターゲット・マシンの Db2

ホスト名: targetdotcom

1. スキーマ `admin2` にテーブル `testdata` を作成します。

2. ユーザー `admin2` として、パスワード
`YYYY` を使用してクラウド・コンソールの Db2 から `testdata`
テーブルとデータを読み込みます。

### ターゲットのクライアント・マシン

1. ターゲット・マシンをカタログに追加します。<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   例えば、以下を行えます。<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. fedS 上のデータベースをカタログに追加します。<br/>
   `db2 catalog db bludb as <db_name> at node <node_name>`

   例えば、以下を行えます。<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. fedS 上のデータベースに接続します。<br/>
   `db2 connect to <catalog_db_name> user <admin_user> using '<admin_password>'`

   例えば、以下を行えます。<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. fedS 上にラッパーを作成します。<br/>
   `db2 "create wrapper drda"`

5. ターゲット・マシンと通信するためのサーバーを作成します。<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   例えば、以下を行えます。<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. admin2 用のユーザー・マッピングを作成します。<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   例えば、以下を行えます。<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. データベースのニックネームを作成します。<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   例えば、以下を行えます。<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### クラウド・ソース・マシンの Db2

1. ターゲット・サーバーからデータを取得できることをテストします。<br/>
   `db2 "select * from <nickname>"`

   例えば、以下を行えます。<br/>
   `db2 "select * from ntest1"`

## 追加情報

データ仮想化 (フェデレーション) について詳しくは、
[
フェデレーション ![外部リンク・アイコ
ン](../../icons/launch-glyph.svg "外部リンク・アイコン
")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window} を参照してください。

フェデレーションでサポートされるデータ・ソースについて詳しくは、
[フェデレーションでサポートさ
れるデータ・ソース ![外部リ
ンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window} を参照してください。

