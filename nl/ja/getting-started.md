---

copyright:
  years: 2014, 2019
lastupdated: "2019-05-23"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 入門チュートリアル
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}} は、ユーザーのためにクラウド内にプロビジョンされている SQL データベースです。 {{site.data.keyword.Db2_on_Cloud_short}} は、他のデータベース・ソフトウェアと同様に使用できますが、ハードウェアのセットアップやソフトウェアのインストールおよび保守の時間や経費は必要ありません。 
{: shortdesc}

資格情報を作成します。 初めて IBM Cloud を使用するユーザーは、サービスを作成した後、サービスの起動時に**「資格情報の作成」**ボタンをクリックして、ユーザー名とパスワードを作成する必要があります。 厳密に言うと、資格情報がなくても Web コンソールにログインすることはできますが、Db2 ツールの多くを使用するためにはユーザー名とパスワードが必要になります。
{: important}

[無料の Db2 Developer Edition ダウンロード](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:external}を使用して、ローカルの Db2 データベースをインストールすることもできます。ここでは、すぐに使用できる Db2 Developer Edition が、Docker コンテナー内のツールとともに速や
かにインストールされます (Docker は不要です。必要なコンポーネントは自動的にインストールされます)。 

## インターフェース
{: #interfaces}

以下の方法で、{{site.data.keyword.Db2_on_Cloud_short}} データベースを使用した作業を行うことができます。
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} Web コンソール
   * REST API
   * ローカル・コンピューターからアプリケーションまたは任意のツールを接続する
   * {{site.data.keyword.Bluemix_notm}} アプリまたはサービス用のデータ・ソースとして {{site.data.keyword.Db2_on_Cloud_short}} を使用する

### Db2 on Cloud Web コンソール
{: #web_console}

Web コンソールは、ロード機能、SQL エディター、ドライバー・ダウンロードなど、データベースを使用するために必要なすべての操作を実行できるグラフィカル・インターフェースです。
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour](http://ibm.biz/dashdb-general-quick-tour){:external}. -->

以下の方法で、{{site.data.keyword.Db2_on_Cloud_short}} Web コンソールにアクセスできます。
   * {{site.data.keyword.Bluemix_notm}} ダッシュボードから - {{site.data.keyword.Db2_on_Cloud_long_notm}} サービスの「サービス詳細」ページから Web コンソールを開くことができます。
   * ダイレクト URL - {{site.data.keyword.Db2_on_Cloud_short}} サービスの Web コンソールの URL をブックマークできます。

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API](http://ibm.biz/dashdb-api){:external}.
{: shortdesc} -->

### ご使用のコンピューターへの Db2 コマンド・ライン・クライアントおよびドライバーのインストール
{: #connect_apps}

ほとんどの場合、ユーザーは REST API のみを使用するか、Python の `pip` コマンドなどを使用してフレームワーク用のドライバーをインストールすることが多いはずです。
{: shortdesc}

MacOS 用の Python ドライバー・パッケージをインストールするには、`--no-cache-dir` オプションを指定して `pip` コマンドを使用する必要があります。 詳細な手順については、[IBM DB2 および IBM Informix の Python サポート](https://ibm.biz/db2-drivers-python){:external}を参照してください。
{: note}

Python を使用してデータ・サイエンスの作業を行っている場合、またはデータ・フレーム、インデータベース分析、あるいは Watson Studio の使用に関してサポートが必要な場合は、代わりに [ibmdbpy 0.1.5](https://pypi.org/project/ibmdbpy/){:external} を使用することをお勧めします。これは、さまざまなデータ・サイエンス機能のサポートを重点に置いたドライバーです。
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:external} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

Python または Node.js フレームワーク・ドライバーをインストールするには、以下のリンクのいずれかをクリックします。
- [Python ドライバー](https://ibm.biz/db2-drivers-python){:external}
- [Node.js ドライバー](https://ibm.biz/db2-drivers-node){:external}

Sequelize という Node.js ORM をインストールするには、以下のリンクをクリックしてください。
[Sequelize](https://github.com/ibmdb/sequelize){:external}
{: note}

Java、Go、Jupyter Notebooks、Ruby、PHP など、その他のドライバー・インストール・オプションについては、以下のリンクをクリックしてください。 

- [ibmdb](https://github.com/ibmdb){:external}

既にフレームワーク・ドライバーをインストールしていると想定される場合は、次の手順はスキップできます。 しかし、パワー・ユーザーは、Db2 コマンド・ライン・クライアントを使用して、データベースを管理し、Db2 コマンドを使用することが必要な場合もあります。 また、特定の ODBC アプリケーションや JDBC アプリケーションは、Db2 ドライバーを汎用インストールすると恩恵を受けることができます。 その場合は、以下のステップを実行してください。

1. アプリまたはツールが実行されているコンピューターで [ドライバー・パッケージのインストール](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:external}を行います。
2. ご使用の {{site.data.keyword.Db2_on_Cloud_short}} データベースに応じて[ドライバー・ファイルの構成](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external}を行います。

### {{site.data.keyword.Bluemix_notm}} アプリまたはサービス用のデータ・ソースとして Db2 on Cloud を使用する
{: #data_src}

{{site.data.keyword.Bluemix_notm}} でホストされているアプリは、ローカル・アプリケーションが {{site.data.keyword.Db2_on_Cloud_short}} データベースに接続するのと同じ方法で、{{site.data.keyword.Db2_on_Cloud_short}} データベースに接続できます。
{: shortdesc}

アプリが {{site.data.keyword.Bluemix_notm}} プラットフォームを使用している場合、`VCAP _SERVICES` 環境変数を利用して、データベースの詳細および資格情報を指定する作業を単純化できます。
1. {{site.data.keyword.Bluemix_notm}} ダッシュボードで、{{site.data.keyword.Db2_on_Cloud_long_notm}} サービスの「サービス詳細」ページの**「接続」**タブで、**「接続の作成」**ボタンをクリックします。
2. {{site.data.keyword.Db2_on_Cloud_short}} データベースをデータ・ソースとして使用する {{site.data.keyword.Bluemix_notm}} アプリを選択し、**「接続」**ボタンをクリックします。
3. データベースの詳細および資格情報を `VCAP_SERVICES` 環境変数から取り出すようにアプリケーション・コードを更新します。

    **`VCAP_SERVICES` を使用しない例**

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

    **`VCAP_SERVICES` を使用する例**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

## 例
{: #samples}

各種の言語で作成されたアプリケーションから {{site.data.keyword.Db2_on_Cloud_short}} データベースに接続する方法を示すサンプルへのリンクは次のとおりです。
{: shortdesc}

   * [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
<!-- * [JAVA](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:external} -->
   * [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
<!-- * [Node.js](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:external} -->
   * [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}
<!-- * [Python](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:external} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:external} -->

## ビデオ: Db2 on Cloud の紹介
{: #intro_vid}

{{site.data.keyword.Db2_on_Cloud_short}} の概要については、このビデオをご覧ください。

<iframe class="embed-responsive-item" id="youtubeplayer1" title="Introduction to {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## ビデオ: REST API を使用した Db2 on Cloud との通信
{: #vid_api}

RESTful API を使用して {{site.data.keyword.Db2_on_Cloud_short}} と通信するために必要な手順を確認するには、このビデオをご覧ください。

<iframe class="embed-responsive-item" id="youtubeplayer2" title="Using RESTful API to communicate with {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## ビデオ: Jupyter ノートブックの統合
{: #cognos_vid}

Jupyter ノートブックを {{site.data.keyword.Db2_on_Cloud_short}} と統合する方法を確認するには、このビデオをご覧ください。

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Integrating Jupyter notebooks" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


