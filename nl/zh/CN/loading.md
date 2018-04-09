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

# 装入数据
{: #load}

您可以从本地网络、对象存储（Amazon S3 或 IBM Cloud Object Storage（以前称为 SoftLayer Swift））上定界格式的数据文件（如 CSV 或 TXT）或者使用 Db2® 工具装入数据。您还可以通过从应用程序（如 InfoSphere® DataStage®）执行装入过程，为数据库实例填充数据。
{: shortdesc}

* [使用 Lift CLI 装入数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://lift.ng.bluemix.net/#docs){:new_window}
* [从 Oracle 装入数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://lift.ng.bluemix.net/#docs){:new_window}
* [从 SQL Server 装入数据 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://lift.ng.bluemix.net/#docs){:new_window}
* [装入 CSV 文件 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* 使用以下一种方法从 Amazon S3 装入数据：
    * {{site.data.keyword.dashdbshort_notm}} Web 控制台。**装入 > Amazon S3**。 
    * 直接从外部表。以下是示例 SQL 语句：

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
