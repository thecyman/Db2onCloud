---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-21"

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

# IBM Cloud での ID およびアクセス管理 (IAM)
{: #iam}

ID およびアクセス管理 (IAM) を使用すると、プラットフォーム・サービスに関してユーザーをセキュアに認証でき、また {{site.data.keyword.Bluemix_notm}} プラットフォーム全体で一貫してリソースへのアクセスを制御できます。 例えば、IBMid を使用して {{site.data.keyword.Bluemix_notm}} に 1 回ログインするだけで、お客様のサービス・コンソールとそのアプリケーションのすべてにアクセスでき、それぞれに個別にログインする必要はありません。
{: shortdesc}

## インスタンスで IAM が使用可能かどうか
{: #enabled}

一定期間にわたって、{{site.data.keyword.Bluemix_notm}} 上で {{site.data.keyword.Db2_on_Cloud_long}} が管理するデータベース・インスタンスでアクセス制御のために IAM を使用できるようになります。 インスタンスで IAM が使用可能になっていることを確認するには、以下の照会を実行します。

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

**IAM_ENABLED** の戻り値が 1 の場合、インスタンスで IAM が使用可能になっています。

## IBM Cloud IAM のフィーチャー
{: #features}

次の 2 つのタイプのサポートされる ID と共に、{{site.data.keyword.Db2_on_Cloud_short}} が管理するサービス用に下記の IAM フィーチャーが実装されています。

**IBMid**

IBMid を持つユーザーが特定のデータベース・サービス・インスタンスに接続できるためには、データベース管理者がコンソールまたは REST API を介してそれらのユーザーを各データベース・サービス・インスタンスに前もって追加しておく必要があります。 非 IBMid ユーザーの場合と同様に、IBMid ユーザーを追加するのと同時にデータベース・サービス・インスタンス用のユーザー ID を入力する必要があります。 このユーザー ID は、データベース・サービス・インスタンス内で固有である必要があります。 このユーザー ID は、データベース内の許可 (AUTH) ID でもあります。 データベース管理者は、AUTH ID に基づいて許可を付与および取り消すことができます。

**サービス ID**

ユーザー ID がユーザーを識別するように、サービス ID はサービスまたはアプリケーションを識別します。 サービス ID は、アプリケーションが IBM Cloud サービスでの認証に使用できる ID です。 サービス ID は、所有している IBMid とは分離したエンティティーを表します。 したがって、異なる権限および許可をデータベース内のサービス ID に固有に付与できます。 サービス ID にはパスワードはありません。 サービス ID がデータベース・サービス・インスタンスに接続するためには、サービス ID ごとに API キーが作成される必要があります。 サービス ID について詳しくは、[Introducing IBM Cloud IAM Service IDs and API Keys ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window} を参照してください。

## クライアント接続およびユーザー・ログイン
{: #connect_user}

**前提条件**: Db2 Client V11.1 FP3 以降。

IAM 認証のために以下の方式を使用できます。

**アクセス・トークン**

API キーを使用して REST API を介して、アプリケーションで直接 IAM サービスからアクセス・トークンを取得できます。 詳しくは、[API キーを使用した IBM Cloud IAM トークンの取得 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/iam?topic=iam-iamtoken_from_apikey#iamtoken_from_apikey){:new_window} を参照してください。 アクセス・トークンのデフォルトの有効期間は 60 分間であり、それを過ぎると期限切れになります。 トークンの有効期限が切れている場合、Db2 サーバーは接続の確立を許可しません。 接続が確立された後はトークンの有効期限は検査されません。 IAM 統合の前と同様に、アプリケーションが切断するか、他の理由で接続が終了されるまで、接続は接続されたままになります。

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

アクセス・トークンは、IBMid ユーザー、またはデータベースへのサービス ID を識別します。 データベース・サーバーは、アクセス・トークンを受け入れる前にその妥当性を検証します。 これは、アプリケーションが複数のデータベース・サービス・インスタンスまたは他の {{site.data.keyword.Bluemix_notm}} サービス・インスタンスに接続する必要がある場合、アクセス・トークンを検証するための IAM サービスとの通信が最小限に抑えられるため、最適な方法です。

**API キー**

IBMid ユーザーまたはサービス ID ごとに複数の API キーを作成できます。 通常、各 API キーが単一のアプリケーション用に作成されます。 これにより、所有する IBMid またはサービス ID が同じデータベース・サービス・インスタンスにユーザーとして追加されている限り、アプリケーションがデータベース・サービス・インスタンスに接続可能になります。 API キーはデータベース内で、所有する IBMid またはサービス ID と同じ権限および許可を持ちます。 アプリケーションへのデータベース接続許可が不要になった場合、対応する API キーを削除できます。 この認証方式では、IAM サービスと直接対話する必要がないため、アクセス・トークンを使用するよりもアプリケーションの変更が少なくて済みます。 API キーの作成と管理について詳しくは、[ユーザー API キーの管理 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/iam?topic=iam-userapikey#userapikey){:new_window} を参照してください。

**IBMid およびパスワード**

IBMid およびパスワードはコンソールへのログインに使用でき、ユーザー ID とパスワードを使用できるのと同様にアプリケーション内で使用することもできます。 組織のログイン・ページへのリダイレクトを実行できないため、IBMid が統合されている場合は例外が発生します。 ただし、アプリケーションがデータベース・サービス・インスタンスへの接続を確立するための推奨方法は、アクセス・トークンを使用することです。

## サポートされるインターフェース
{: #sup-if}

以下のデータベース・クライアント・インターフェースがサポートされます。

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC、CLP、および CLPPLUS
{: #odbc-clpplus}

ODBC アプリケーションまたはコマンド・ライン・クライアント (CLP、CLPPLUS) が IAM 認証を使用して Db2 サーバーに接続するためには、まず以下のコマンドを実行して `db2dsdriver.cfg` 構成ファイル内にデータ・ソース名 (DSN) を構成する必要があります。

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

`db2dsdriver.cfg` 構成ファイルは通常は `sqllib/cfg` ディレクトリーにある XML ファイルであり、DSN 別名とそのプロパティーのリストが含まれます。

以下の `db2dsdriver.cfg` 構成ファイル例は、データベース・サービス・インスタンスへの接続を確立するために使用される構成を示しています。 構成ファイルでは、DSN 別名、データベース名、ホスト名 (または IP アドレス)、および **Authentication** タイプと **SecurityTransportMode** パラメーターの値が指定されます。

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

* ODBC 接続ストリングには、以下のいずれかを含めることができます。

    **アクセス・トークン**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **API キー**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBMid およびパスワード**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    ODBC の場合、**AUTHENTICATION=GSSPLUGIN** を、`db2dsdriver.cfg` 構成ファイル内に指定するか、またはアプリケーションの接続ストリングに指定できます。

* CLP CONNECT ステートメントには、以下のいずれかを含めることができます。

    **アクセス・トークン**

    CLP コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、データベース・サーバー `<database_server_name>` に接続して、アクセス・トークンを渡します。

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **API キー**

    CLP コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、API キーを使用してデータベース・サーバー `<database_server_name>` に接続します。

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBMid およびパスワード**

    CLP コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、IBMid およびパスワードを使用してデータベース・サーバー `<database_server_name>` に接続します。

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    CLP を使用したデータベース・サーバーへの接続について詳しくは、[CONNECT (タイプ 2) ステートメント ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window} を参照してください。 

* CLPPLUS CONNECT ステートメントには、以下のいずれかを含めることができます。

    **アクセス・トークン**

    CLPPLUS コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、アクセス・トークンを渡して DSN 別名 (`@<data_source_name>`) に接続します。

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **API キー**

    CLPPLUS コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、API キーを使用して DSN 別名 (`@<data_source_name>`) に接続します。

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBMid およびパスワード**

    CLPPLUS コマンド・プロンプトまたはスクリプトで以下のコマンドを実行することによって、IBMid およびパスワードを使用して DSN 別名 (`@<data_source_name>`) に接続します。

    `connect <IBMid>/<password>@<data_source_name>`

    CLPPLUS を使用した DSN 別名への接続について詳しくは、[CLPPlus での DSN 別名 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.clpplus.doc/doc/c0057148.html){:new_window} を参照してください。

### JDBC
{: #jdbc}

IAM 認証用にタイプ 4 JDBC ドライバーがサポートされています。

3 つの方式の接続スニペットの例を以下に示します。

**アクセス・トークン**

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

または

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**API キー**

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

または

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apiKey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBMid およびパスワード**

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

または

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## コンソール・ユーザー・エクスペリエンス
{: #console-ux}

サービス・コンソールのログイン・ページには、IBMid とパスワードを使用してログインするオプションがあります。 **「IBMid を使用してサインイン」**ボタンをクリックすると、ユーザーは IAM ログイン・ページに誘導され、そこでパスワードを入力します。 認証が完了すると、ユーザーはコンソールに戻ります。 このようなログインが成功するためには、コンソールまたは REST API を介してデータベース管理者が IBMid ユーザーを各データベース・サービス・インスタンスに前もって追加しておく必要があります。 非 IBMid ユーザーの場合と同様に、IBMid ユーザーを追加するのと同時にデータベース・サービス・インスタンス用のユーザー ID を入力する必要があります。 ユーザー ID は、データベース・サービス・インスタンス内で固有である必要があります。 このユーザー ID は、データベース内の許可 (AUTH) ID でもあります。

## REST API エクスペリエンス
{: #api}

{{site.data.keyword.Db2_on_Cloud_short}} REST API の機能が拡張され、前はデータベース・サービスが生成したアクセス・トークンを受け入れていた関数で IAM アクセス・トークンも受け入れるようになりました。

* 新規 IBMid ユーザーを追加するには、以下の例のような API 呼び出しを実行します。

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  `"id"` と `"ibmid"` の `<userid>` 値が同じである必要はありません。 この 2 つの異なる ID がリンクされることはありません。
  {: note}

* 既存の非 IBMid データベース・ユーザー (例えば、`abcuser`) をマイグレーションして IBMid ユーザーにするには、最初に、以下の例のような API 呼び出しを実行して、非 IBMid ユーザー ID を削除します。

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  次に、以下の例のような API 呼び出しを実行して、先のユーザー ID (`abcuser`) と同じ IBMid でユーザーを再追加します。

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  ユーザー ID (`abcuser`) はそのユーザーの新規 IBMid と同じままであるため、このユーザーに付与されたデータベース許可に変更はありません。 一連の既存の非 IBMid データベース・ユーザーをマイグレーションして IBMid ユーザーにする必要がある場合は、ユーザーごとに上記の API 呼び出しのペアを実行する必要があります。

* 一度に多数の新規 IBMid ユーザーを追加するには、ユーザーごとに 1 つずつ以下の例のような API 呼び出しがリストされているバッチ・ファイルを作成します。

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

サービスの API について詳しくは、[{{site.data.keyword.Db2_on_Cloud_short}} REST API ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://ibm.biz/db2oc_api){:new_window} を参照してください。

## IBMid 統合
{: #fed_ibmid}

LDAP などの独自の ID プロバイダーを使用するには、まず LDAP サーバーを IBMid と統合する必要があります。 LDAP サーバーと IBMid の統合の手順については、[IBMid Enterprise Federation Adoption Guide ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.ent.box.com/notes/78040808400?v=IBMid-Federation-Guide){:new_window} を参照してください。 IBMid 統合が完了し、許可されるユーザーがデータベース管理者によってデータベース・サービス・インスタンスに追加された後、これらのユーザーは会社のユーザー ID とパスワードを使用してコンソールにログインできます。 あるいは、これらのユーザーは、ユーザー ID を表すアクセス・トークンまたは API キーを使用して、サポートされるデータベース・クライアント・インターフェースの 1 つを介してデータベース・サービス・インスタンスに接続できます。

## 制約事項
{: #restrictions}

IAM 認証に関して、以下の制約事項があります。

* Db2 サーバーに接続しようとしている Db2 クライアントの IAM 認証は SSL 接続を介してのみサポートされます。
* IBMid 統合は、カスタムのユーザー管理ポータルまたはサーバーを認証に使用できるようにするためにサポートされます。 このようなサポートには、グループ統合は含まれません。
* データベース統合用の IAM 認証はサポートされていません。
* CLPPlus を介した IDA およびユーザー定義拡張 (UDX) コマンドの実行はサポートされていません。
* タイプ 2 JDBC ドライバーはサポートされていません。




