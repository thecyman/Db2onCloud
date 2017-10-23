---

copyright:
  years: 2014, 2017
lastupdated: "2017-09-28"

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

#Db2 on Cloud (旧 dashDB for Transactions) の概説
{: #getting_started_db2oncloud}

{{site.data.keyword.Db2_on_Cloud_long}} は、クラウド内でプロビジョンされた SQL データベースです。任意のデータベース・ソフトウェアを使用するのと同じように {{site.data.keyword.Db2_on_Cloud_short}} を使用できますが、ハードウェアのセットアップやソフトウェアのインストールおよび保守のためのオーバーヘッドもコストもかかりません。
{: shortdesc}

また、ローカルの Db2 データベースを [ 無料の Db2 Developer Edition （![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions) からダウンロードできます。) を使用してインストールすることもできます。 それは Docker コンテナー内のツールとともに Db2 のすぐに使用できる Developer Edition を速やかにインストールします (Docker は不要です。必要なコンポーネントは自動的にインストールされます)。 

##インターフェース
{: #interfaces}

以下の方法で、{{site.data.keyword.Db2_on_Cloud_short}} データベースを使用した作業を行うことができます。
{: shortdesc}

   * {{site.data.keyword.Db2_on_Cloud_short}} Web コンソール
<!--   * REST APIs -->
   * ローカル・コンピューターからアプリケーションまたは任意のツールを接続する
   * Bluemix アプリまたはサービス用のデータ・ソースとして {{site.data.keyword.Db2_on_Cloud_short}} を使用する

###Db2 on Cloud Web コンソール
{: #web_console}

Web コンソールは、ロード機能、SQL エディター、ドライバー・ダウンロードなど、データベースを使用するために必要なすべての操作を実行できるグラフィカル・インターフェースです。
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour){:new_window}. -->

以下の方法で、{{site.data.keyword.Db2_on_Cloud_short}} Web コンソールにアクセスできます。
   * {{site.data.keyword.Bluemix_notm}} ダッシュボードから - {{site.data.keyword.Db2_on_Cloud_long_notm}} サービスの「サービス詳細」ページから Web コンソールを開くことができます。
   * ダイレクト URL - {{site.data.keyword.Db2_on_Cloud_short}} サービスの Web コンソールの URL をブックマークできます。

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

###ローカル・コンピューターからアプリケーションまたは任意のツールを接続する
{: #connect_apps}

以下の手順を実行して、{{site.data.keyword.Db2_on_Cloud_short}} データベースに接続するようにローカル環境を構成します。
{: shortdesc}

1. {{site.data.keyword.Db2_on_Cloud_short}} Web コンソールの「接続情報 (Connection info)」ページから[ドライバー・パッケージ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:new_window} をダウンロードします。
2. アプリまたはツールが実行されているコンピューターで [ドライバー・パッケージのインストール![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:new_window} を行います。
3. {{site.data.keyword.Db2_on_Cloud_short}} データベース用に[ドライバー・ファイルの構成 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window} を行います。

###Bluemix アプリまたはサービス用のデータ・ソースとして Db2 on Cloud を使用する
{: #data_src}

{{site.data.keyword.Bluemix_notm}} でホストされているアプリは、ローカル・アプリケーションが {{site.data.keyword.Db2_on_Cloud_short}} データベースに接続するのとまったく同じ方法で、{{site.data.keyword.Db2_on_Cloud_short}} データベースに接続できます。
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

##例
{: #samples}

各種の言語で作成されたアプリケーションから {{site.data.keyword.Db2_on_Cloud_short}} データベースに接続する方法を示すサンプルへのリンクは次のとおりです。
{: shortdesc}

   * [.NET ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:new_window} -->
   * [JDBC ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:new_window} -->
   * [PHP ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:new_window} -->
   * [GitHub にある {{site.data.keyword.Db2_on_Cloud_short}} サンプル![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:new_window}


