---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-11"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# IBM Cloud로 데이터 마이그레이션
{: #migration}

로컬 네트워크에 있는 CSV 또는 TXT와 같은 구분된 형식의 데이터 파일이나 오브젝트 저장소(Amazon S3 또는 IBM Cloud Object Storage)에서 {{site.data.keyword.Db2_on_Cloud_long}}로 데이터를 로드할 수 있습니다. 온프레미스 시스템에서 데이터를 마이그레이션할 수도 있습니다.
{: shortdesc}

## 오브젝트 저장소에서 데이터 로드
{: #cos}

Amazon S3에서 데이터를 로드하려면 다음 방법 중 하나를 선택하십시오.
  * {{site.data.keyword.Db2_on_Cloud_short}} 웹 콘솔 사용. **로드 > Amazon S3**. 
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

외부 테이블을 직접 사용하여 IBM Cloud Object Storage에서 데이터를 로드하려는 경우 SQL문의 예는 다음과 같습니다.

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )      
```

**참고:** IBM Cloud Object Storage의 경우 새 서비스 신임 정보를 작성할 때 HMAC 신임 정보를 작성하려면 *인라인 구성 매개변수 추가* 필드에 {"HMAC:true"}를 지정하십시오.

## 온프레미스 시스템에서 데이터 마이그레이션
{: #onprem}

온프레미스 시스템에서 데이터를 마이그레이션하려면 데이터 세트 크기에 따라 다음 방법 중 하나를 선택하십시오.
* 25TB 미만의 데이터: [IBM Lift CLI](#lift)
* 25TB 이상의 데이터: [IBM Cloud Mass Data Migration](#mdms)

### Lift CLI
{: #lift}

Lift CLI는 표 1에 나열된 다양한 데이터 소스에서 {{site.data.keyword.Bluemix_notm}}로 데이터를 마이그레이션할때 무료로 사용할 수 있는 애플리케이션입니다. 

| IBM Cloud의 대상 데이터베이스 | 데이터 소스 |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle Database |
|                              | Microsoft SQL Server |
|                              | CSV 파일 형식 |
{: caption="표 1. 데이터 소스 마이그레이션" caption-side="top"}

Lift CLI를 다운로드하고 설치하려면 [Lift CLI 다운로드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#download){:new_window}를 참조하십시오.

Lift CLI를 사용하여 {{site.data.keyword.Bluemix_notm}}로 사용자의 데이터를 마이그레이션하는 방법에 관한 단계별 지시사항은 [Migrate data to {{site.data.keyword.Db2_on_Cloud_long_notm}} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://lift.ng.bluemix.net/#docs){:new_window}의 내용을 참조하십시오.

### IBM Cloud Mass Data Migration
{: #mdms}

실제로 테라바이트부터 페타바이트까지의 데이터를 {{site.data.keyword.Bluemix_notm}}로 전송하는 빠르고 단순하며 안전한 방법입니다. Mass Data Migration은 {{site.data.keyword.Bluemix_notm}}로 데이터 이동을 가속화하는, 120TB의 스토리지 용량이 사용 가능한 모바일 스토리지 디바이스입니다. 단일 서비스의 고비용, 긴 전송 시간 및 보안 문제와 같은 일반적인 전송 문제를 해결합니다.

![Mass Data Migration 디바이스 보기](images/mdms.svg)

Mass Data Migration 디바이스에 대한 자세한 정보는 [IBM Cloud Mass Data Migration 시작하기](/docs/infrastructure/mass-data-migration/index.html#getting-started-with-ibm-cloud-mass-data-migration){:new_window}를 참조하십시오.

