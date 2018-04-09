---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-23"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# データのロード
{: #load}

ローカル・ネットワーク、オブジェクト・ストア (Amazon S3 または IBM Cloud オブジェクト・ストレージ (以前の SoftLayer Swift)) 上にある、区切り文字で区切られた形式の CSV や TXT などのデータ・ファイルのデータをロードできます。あるいは、DB2® ツールを使用できます。また、InfoSphere® DataStage® などのアプリケーションからロード・プロセスを実行して、データベース・インスタンスにデータを設定することもできます。
{: shortdesc}

* [Lift CLI を使用したデータのロード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Oracle からのデータのロード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lift.ng.bluemix.net/#docs){:new_window}
* [SQL Server からのデータのロード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lift.ng.bluemix.net/#docs){:new_window}
* [CSV ファイルのロード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* 次のいずれかの方法を使用して、Amazon S3 からデータをロードします。
    * {{site.data.keyword.dashdbshort_notm}} Web コンソール。**「ロード (Load)」 > 「Amazon S3」**。 
    * 外部のテーブルから直接。次に、SQL ステートメントの例を示します。

    ```
      INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
        (CCSID 1208 s3('s3.amazonaws.com', 
        '<S3-access-key-ID>',
        '<S3-secret-access-key>', 
        '<my_bucket>'
           )
        )      
    ```
<!-- * [Loading data from Amazon S3 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/s3.html){:new_window} -->
