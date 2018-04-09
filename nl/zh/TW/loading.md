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

# 載入資料
{: #load}

您可以從位於本端網路的定界格式資料檔案（例如 CSV 或 TXT）、物件儲存庫（Amazon S3 或 IBM Cloud Object Storage（先前稱為 SoftLayer Swift））或藉由使用 Db2® 工具來載入資料。您也可以將資料移入資料庫實例，方法是從例如 InfoSphere® DataStage® 的應用程式執行載入處理程序。
{: shortdesc}

* [使用 Lift CLI 載入資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://lift.ng.bluemix.net/#docs){:new_window}
* [從 Oracle 載入資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://lift.ng.bluemix.net/#docs){:new_window}
* [從 SQL Server 載入資料 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://lift.ng.bluemix.net/#docs){:new_window}
* [載入 CSV 檔案 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* 使用下列其中一種方法，從 Amazon S3 載入資料：
    * {{site.data.keyword.dashdbshort_notm}} Web 主控台。**載入 > Amazon S3**。 
    * 直接從外部表格。以下是範例 SQL 陳述式：

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
