---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# 백업 및 복원
{: #bnr}

유료 플랜의 경우 데이터베이스의 암호화된 백업이 매일 수행됩니다. 지난 14일 동안의 일별 백업이 보관됩니다.
{: shortdesc}

표준 백업 외에도 [Time Travel Query ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window}를 사용하여 이전 데이터를 즉시 조회하거나 단순 감사에 사용하는 등의 기타 용도로 히스토리 데이터를 보존할 수 있습니다. IBM Data Studio 또는 임의 Db2 도구를 사용하여 고유 내보내기를 수행할 수 있습니다.
 
특정 시점 복원에 관한 정보는 [특정 시점 복원](#point-in-time)을 참조하십시오.

일반적으로 모든 유료 플랜에서 IBM COS(Cloud Object Storage)를 사용하여 3개의 서로 다른 데이터 센터에서 오프사이트로 백업을 유지합니다. 그러나 시드니와 특정 소규모 데이터 센터에서는 현재 IBM COS를 사용한 오프사이트 복제를 지원하지 않습니다. 오프사이트 복제를 지원하는 지역을 판별하려면 사용자 지역의 [IBM COS 문서](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-endpoints#endpoints)를 확인하십시오.

[IBM Lift CLI ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.lift-cli.cloud.ibm.com/){:new_window}를 사용하여 데이터를 {{site.data.keyword.Db2_on_Cloud_short}}에 가져올 수도 있습니다.

## 특정 시점 복원
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}}에는 특정 시점 복원 기능이 추가되었습니다. 백업에서 정확하게 특정 시점으로 복원할 수 있습니다. 현재 대부분의 고객은 이 기능을 활성화하도록 지원 센터에 요청해야 합니다. 다음 롤아웃 스케줄을 참조하십시오.

다음은 특정 시점 복원 기능의 가용성 목록입니다.
- 달라스 데이터 센터: 단일 서버 시스템에서 현재 사용 가능
- 유럽과 달라스에 있는 HA 시스템을 포함하는 기타 모든 경우: 지원 센터에서 기능 활성화를 요청하십시오. 2019년 2월 28일까지 모든 시스템에 완전히 롤아웃될 예정입니다.
- IBM Cloud Dedicated 시스템: 지원 티켓을 열어야만 사용할 수 있습니다. 

다음은 특정 시점 복원 조작이 시작되고 해당 진행상태가 표시되는 웹 콘솔 UI의 스크린샷 중 선택된 몇 가지 예입니다.

1. **특정 시점** 복원 전략을 선택하고 데이터베이스를 복원할 특정 시점 날짜를 선택하십시오. 특정 시점 복원 프로세스에서는 지난 14일 동안 보유한 백업 풀 중에서 요청된 특정 시점 날짜와 가장 가까운 백업을 선택합니다. 

   결과적으로 타임라인에 차이가 생기므로 특정 시점 복원 프로세스에서는 이전에 보유한 백업 중 날짜가 선택한 특정 시점 날짜 이후인 백업은 모두 무효화합니다.
   {: note}

   ![특정 시점 복원 전략의 강조표시된 선택사항 보기](images/pit_restore_1.png)

2. 복원 선택사항을 계속하는지 확인하십시오. 복원 조작을 시작하고 나면 요청을 변경할 수 없습니다.  
![특정 시점 복원 확인 대화 상자 보기](images/pit_restore_2.png)

3. 복원 프로세스가 초기화 중입니다.
![특정 시점 복원 초기화 보기](images/pit_restore_3.png)

4. 선택한 시점으로 데이터베이스를 복원합니다.
![특정 시점 복원의 진행상태 보기](images/pit_restore_4.png)

5. 새 백업 지점을 작성 중입니다. 특정 시점으로 복원된 데이터베이스를 사용할 준비가 되었습니다.
![새 백업 지점 작성 보기](images/pit_restore_5.png)

6. 복원 조작이 완료되었습니다.
![복원 조작의 성공적 완료 보기](images/pit_restore_6.png)

