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

# 데이터 로드
{: #load}

로컬 네트워크에 있는 CSV 또는 TXT와 같은 구분된 형식의 데이터 파일이나 오브젝트 스토어(Amazon S3 또는 IBM Cloud Object Storage(이전 이름:SoftLayer Swift))에서 또는 Db2® 도구를 사용하여 데이터를 로드할 수 있습니다. 또한 InfoSphere® DataStage®와 같은 애플리케이션에서 로드 프로세스를 수행하여 데이터베이스 인스턴스를 데이터로 채울 수 있습니다.
{: shortdesc}

* [Loading data with Lift CLI ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading data from Oracle ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading data from SQL Server ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading a CSV file ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* 다음 방법 중 하나를 사용하여 Amazon S3에서 데이터를 로드하십시오.
    * {{site.data.keyword.dashdbshort_notm}} 웹 콘솔 사용. **로드 > Amazon S3**. 
    * 외부 테이블 직접 사용. 다음은 SQL문의 예제입니다.

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
