---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 将数据迁移至 IBM Cloud
{: #migration}

您可以从本地网络或对象存储（Amazon S3 或 IBM Cloud Object Storage）上定界格式的数据文件（CSV 或 TXT）将数据装入到 {{site.data.keyword.Db2_on_Cloud_long}}。您甚至可以从内部部署系统迁移数据。
{: shortdesc}

## 从对象存储装入数据
{: #cos}

要从 Amazon S3 装入数据，请选择以下其中一种方法：
  * {{site.data.keyword.Db2_on_Cloud_short}} Web 控制台。**装入 > Amazon S3**。 
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

要使用“外部表”直接从 IBM Cloud Object Storage 装入数据，以下是示例 SQL 语句：

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net',
  '<S3-access-key-ID>',
  '<S3-secret-access-key>',
  '<my_bucket>'
     )
  )      
```

对于 IBM Cloud Object Storage，要在创建新服务凭证时创建 HMAC 凭证，请在*添加内联配置参数*字段中指定 {"HMAC:true"}。
{: note}

## 从内部部署系统迁移数据
{: #onprem}

要从内部部署系统迁移数据，请根据数据集大小，选择以下其中一种方法：
* 小于 25 TB 的数据：[IBM Lift CLI](#lift)
* 25 TB 及更多的数据：[IBM Cloud Mass Data Migration](#mdms)

### Lift CLI
{: #lift}

Lift CLI 是可免费使用的应用程序，用于将数据从表 1 中列出的各个数据源迁移至 {{site.data.keyword.Bluemix_notm}}。 

| IBM Cloud 上的目标数据库     | 数据源      |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle 数据库 |
|                              | Microsoft SQL Server |
|                              | CSV 文件格式 |
{: caption="表 1. 迁移数据源" caption-side="top"}

要下载并安装 Lift CLI，请参阅：[Download Lift CLI](https://www.lift-cli.cloud.ibm.com/#download){:external}。

有关使用 Lift CLI 将数据迁移至 {{site.data.keyword.Bluemix_notm}} 的逐步指示信息，请参阅：[将数据迁移至 {{site.data.keyword.Db2_on_Cloud_long_notm}}](https://www.lift-cli.cloud.ibm.com/#docs){:external}。

### IBM Cloud Mass Data Migration
{: #mdms}

通过物理方式将上万亿字节到上千万亿字节的数据传输到 {{site.data.keyword.Bluemix_notm}}，既快速简单又安全。Mass Data Migration 是具有 120 TB 可用存储容量的移动存储设备，可加速数据移动至 {{site.data.keyword.Bluemix_notm}} 的过程。能够克服常见的传输挑战，例如，成本高、传输时间长和安全问题 - 一个服务解决所有难题。

![Mass Data Migration 设备的视图](images/mdms.svg "Mass Data Migration 设备的视图")

有关 Mass Data Migration 设备的更多信息，请参阅：[入门教程](/docs/infrastructure/mass-data-migration?topic=mass-data-migration-getting-started-tutorial#getting-started-with-ibm-cloud-mass-data-migration){:external}。

