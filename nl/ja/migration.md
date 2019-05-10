---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

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

# IBM Cloud へのデータ・マイグレーション
{: #migration}

ローカル・ネットワーク上またはオブジェクト・ストア内 (Amazon S3 または IBM Cloud Object
Storage) にある、区切り文字で区切られた形式 (CSV または TXT) のデータ・ファイルから
{{site.data.keyword.Db2_on_Cloud_long}} にデータをロードできます。 オンプレミス・システムからデータをマ
イグレーションすることもできます。
{: shortdesc}

## オブジェクト・ストアからのデータのロード
{: #cos}

Amazon S3 からデータをロードするには、以下のいずれかの方法を選択します。
  * {{site.data.keyword.Db2_on_Cloud_short}} Web コンソール。 **「ロード (Load)」 > 「Amazon S3」**。 
  * 外部のテーブルから直接。 次に、SQL ステートメントの例を示します。

    ```
    INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
      (CCSID 1208 s3('s3.amazonaws.com', 
      '<S3-access-key-ID>',
      '<S3-secret-access-key>', 
      '<my_bucket>'
         )
      )      
    ```

外部表を使用して、IBM Cloud Object Storage から直接データをロードする場合、以下のサンプル
SQL ステートメントを使用できます。

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )      
```

IBM Cloud Object Storage の場合、HMAC 資格情報を作成するために、新規サービス資格情報を作成する際、*「インラインの構成パラメーターの追加」*フィールドに {"HMAC:true"} を指定してください。
{: note}

## オンプレミス・システムからのデータのマイグレーション
{: #onprem}

オンプレミス・システムからデータをマイグレーションするには、データ・セットのサイズに応じて
、以下のいずれかの方式を選択します。
* 25 TB 未満のデータ: [IBM Lift CLI](#lift)
* 25 TB 以上のデータ: [IBM Cloud Mass Data
Migration](#mdms)

### Lift CLI
{: #lift}

Lift CLIは、表 1 にリストされている各種データ・ソースから
{{site.data.keyword.Bluemix_notm}} にデータをマイグレーションするときに無料で使用できるア
プリケーションです。 

| IBM Cloud 上のターゲット DB | データ・ソース |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle データベース |
|                              | Microsoft SQL Server |
|                              | CSV ファイル・フォーマット |
{: caption="表 1. マイグレーションのデータ・ソース" caption-side="top"}

Lift CLI のダウンロードとインストールについては、[Lift CLI のダウンロード![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.lift-cli.cloud.ibm.com/#download){:new_window} を参照してください。


Lift CLI を使用して {{site.data.keyword.Bluemix_notm}} にデータをマイグレーションする手順については、[{{site.data.keyword.Db2_on_Cloud_long_notm}} へのデータ・マイグレーション
![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.lift-cli.cloud.ibm.com/#docs){:new_window} を参照してください。

### IBM Cloud Mass Data Migration
{: #mdms}

テラバイト単位からペタバイト単位までのデータを {{site.data.keyword.Bluemix_notm}}
に物理的に転送するための高速でシンプルで安全な方法です。 Mass Data Migrationは 120 TB の使用可能な記憶容量を備えたモ
バイル・ストレージ・デバイスで、{{site.data.keyword.Bluemix_notm}} へのデータ移動を高速化す
ることが
できます。 高いコスト、長い転送時間、セキュリティー上の懸念など、転送に関する共通の
な課題を単一のサービスですべて克服できます。

![Mass Data Migration デバイスの外観](images/mdms.svg)

Mass Data Migration デバイスについて詳しくは、
[入門チュートリアル](/docs/infrastructure/mass-data-migration?topic=mass-data-migration-getting-started-tutorial#getting-started-with-ibm-cloud-mass-data-migration){:new_window} を参照してください。

