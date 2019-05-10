---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# 무료 플랜
{: #free_plan}

{{site.data.keyword.Db2_on_Cloud_long}} 무료 플랜에서는 Db2를 개발하거나 학습하는 데 사용할 수 있는 기본 리소스를 무료로 제공합니다.
{: shortdesc}

무료 플랜에 시간 제한은 없지만 사용자는 30일마다 무료 플랜을 재연장해야 합니다.

커뮤니티 지원만 사용 가능합니다. 
 
## 아키텍처
{: #architecture}

다른 {{site.data.keyword.Db2_on_Cloud_short}} 플랜과 달리 {{site.data.keyword.Db2_on_Cloud_short}} 무료 플랜은 멀티 테넌트 시스템에서 실행됩니다. Flex 및 Precise Performance 플랜은 고유의 싱글테넌트 가상 머신 또는 베어메탈 서버에서 실행됩니다.
 
무료 플랜을 사용하면 하나의 데이터베이스 스키마를 사용할 수 있습니다.

{{site.data.keyword.Db2_on_Cloud_short}} 무료 플랜에 관한 자세한 정보는 [FAQ ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oc_free_plan_faq){:new_window}를 참조하십시오.

## 북아메리카 대륙 이외의 지역에서 무료 플랜 사용
{: #outside_na}

무료 플랜은 현재 북아메리카 대륙의 신용카드를 사용하지 않고도 액세스 가능합니다. 북아메리카 대륙 이외의 지역 고객은 IBM Cloud 계정에 신용카드를 추가한 다음, 선택사항에 무료 플랜이 표시되도록 "미국 남부 - 댈러스" 지역을 선택하십시오.

무료 플랜은 항상 무료이며 신용카드로 비용이 청구되지 않습니다.

## 무료 플랜 제한사항
{: #fp_restrictions}

미션을 이행하는 데 중요하거나 성능에 민감한 워크로드의 경우 무료 서비스 플랜이 아니라 엔터프라이즈 레벨 서비스 플랜을 사용하는 것이 좋습니다. 
{: important}

다음은 {{site.data.keyword.Db2_on_Cloud_short}} 무료 플랜 제한사항을 나타내는 표입니다.

| 카테고리 | 항목 | 제한사항 | 
|----------|------|-------------|
| 리소스 | 스토리지 | 사용자당 200MB의 스토리지 |
|  | 연결 | 사용자당 5개의 연결 |
|  | 성능 | 다중 테넌트 시스템에서 다른 사용자가 실행하는 워크로드 때문에 성능이 변동될 수 있음 |
|  |  |
| 특징 & 기능 | 연합 |지원되지 않음 |
|  | Oracle 호환성 |지원되지 않음 |
|  | 사용자 정의 확장기능(UDF) | 무료 플랜을 포함하여 모든 {{site.data.keyword.Db2_on_Cloud_short}} 플랜에서 지원되지 않음 |
|  | 사용자 관리 | 사용자에게 관리 권한이 부여되지 않음 |
|  | 행 및 열 액세스 제어(RCAC) |지원되지 않음 |
|  | 데이터 로드에 사용하는 IBM InfoSphere Data Replication |지원되지 않음 |
|  |  |
| 네트워킹 환경 | IBM Cloud Integrated Analytics |지원되지 않음 |
|  | IBM Cloud Dedicated |지원되지 않음 |
|  |  |
| 보안 준수 | HIPAA(Health Information Portability and Accountability Act of 1996) | 지원되지 않음. 서비스 설명을 참조하십시오. |
|  | EU 일반 개인정보 보호법률(GDPR) | 지원되지 않음. 서비스 설명을 참조하십시오. |
|  |  |
| 계정 관리 | 재활성화 | 30일마다 재활성화해야 합니다. 재활성화하지 않으면 60일 이후에 무료 플랜 서비스가 삭제됩니다.  |
{: caption="표 1. {{site.data.keyword.Db2_on_Cloud_short}} 무료 플랜 제한사항" caption-side="top"}


