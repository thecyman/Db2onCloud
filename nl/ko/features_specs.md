---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-05"

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

# 기능 & 사양
{: #fs}

{{site.data.keyword.Db2_on_Cloud_long}} 기능과 사양은 사용자 편의를 위해 여기에 요약되어 있습니다.
{: shortdesc}

| 카테고리 | 기능 | 지원 여부? | 설명 |
|----------|---------|------------|----------|
|일반사항 | Db2 AESE |Y | Db2 v11.1.3.3 |
|  | 대기 중 읽기 |Y | 오프사이트 DR 노드만 해당 |
|  | 자동 롤링 업데이트 |Y | HA 플랜 포함 |
|  | 데이터 센터 위치 옵션 |Y | [위치 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-locations){:new_window}. 배치 & 스케일링 기간도 참조하십시오. |
|  | BLU 인메모리 |Y | 기본값은 행입니다. BLU에 대해 `CREATE TABLE..AS COL`을 지정하십시오. |
|  | 활동 트래커 | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | 루트 액세스 제공 | N | 루트 액세스가 필요한 경우 Db2 Hosted 사용 |
|  |  |  |  |
| 고가용성 & 복제 | 오프사이트 DR |Y | - |
|  | 고가용성(한 구역에 노드 2개) |Y | 99.99% 가동 시간 SLA |
|  | 동일한 데이터 센터의 다른 구역 | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | **참고**: 오프사이트 HADR을 사용할 수 있음 |
|  | CDC(Change Data Capture) |Y | - |
|  | 온프레미스에서 HADR로 사용 | N | CDC를 사용하십시오. 자세한 정보는 [Db2에서 Db2 on Cloud로 어떻게 데이터를 마이그레이션하거나 동기화할 수 있습니까? ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window}를 참조하십시오. |
|  | 자율 장애 복구 - HA |Y | - |
|  | 자율 장애 복구 - 오프사이트 DR | N | 단추 또는 API 사용 |
|  | 장애 복구로 IP 이동 |Y | 로컬 HA만 해당, 오프사이트 HADR 아님 |
|  | RPO: 고가용성 | 0s | HA는 동기식임 |
|  | RTO: 고가용성 | 일반적으로 0-10분 | 재시도 코드를 사용하면 Db2 ACR을 사용할 때 느림으로 표시됩니다. |
|  | RPO: 오프사이트 노드 HADR | 일반적으로 < 15s | 오프사이트 DR이 비동기식임 |
|  | RTO: 오프사이트 노드 HADR | < 3분 | 콘솔 단추 또는 API를 사용하여 시작해야 함 |
|  |  |  |  |
| 시스템 구성 | 최대 RAM 및 코어 수 | 1TB RAM, 48개의 코어 | Precise Performance XL 플랜에 적용 |
|  | 최대 스토리지 | 11TB | Precise Performance XL 플랜에 적용됩니다. 데이터와 로그 모두에 사용할 디스크입니다. |
|  | Flex: 기본 플랜 | 4GB RAM, 1개의 코어, 2GB 디스크 | - |
|  | Flex: 최대 RAM 및 코어 수 | 128GB RAM, 32개의 코어 | 더 높은 사양이 필요하십니까? Precise Performance 플랜을 사용하거나 IBM 지원 센터에 문의하십시오. |
|  | Flex: 최대 스토리지 | 4TB |데이터와 로그 모두에 사용할 디스크입니다.  더 높은 사양이 필요하십니까? Precise Performance 플랜을 사용하거나 IBM 지원 센터에 문의하십시오. |
|  |  |  |  |
| 유지보수 정책 & SLA | 고가용성 플랜 | 99.99% | - |
|  | 단일 서버 플랜 | 99.5% | - |
|  | 오프사이트 DR만 해당 | 99.5% | 99.99% 달성을 위해서는 추가 로컬 HA를 사용해야 함 |
|  |유지보수 정책 |Y | [세부사항 읽기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| 보안 준수 | HIPAA 준비 |Y | Flex 등의 모든 유료 플랜. IBM Support에서 HIPAA 모드를 요청해야 합니다. <!--For Db2 Warehouse on Cloud [see docs here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Db2whc/index.html#getting_started){:new_window}.--> |
|  | HITRUST  | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | 이제 HITRUST에 Db2 Hosted를 사용할 수 있음 |
|  | 국제 표준화 기구(ISO)  |Y | ISO 27001, 27002, 27017 및 27018 |
|  | SOC(Service Organization Controls)) |Y | SOC 2 유형 2 |
|  |GDPR |Y | - |
|  | EU Cloud |Y |프랑크프루트 지역을 사용합니다. EU에서 물리적으로 지원이 제공됩니다. |
|  | 전체 준수 목록 |Y | [보안 준수 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| 백업 & 복원 | 일별 백업 |Y | 14일 동안의 일별 백업 |
|  | 특정 시점 자체 복구 | 2018년 11월 15일부터 사용 가능 | [특정 시점 복원](/docs/services/Db2onCloud/br.html#point-in-time) |
|  | 오프사이트에 백업 보관 | 요청 시 | 2018년 12월 1일부터 사용 가능. 오프사이트가 기본값입니다.  |
|  | 최대 10년까지 백업 보관 | 요청 시 | 2018년 12월 1일부터 사용 가능. 지원 티켓이 필요합니다. |
|  | 복원 없이 이전 데이터 조회 |Y | [Time Travel Query ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window}를 설정해야 합니다. |
|  |  |  |  |
| 네트워킹, 보안 & VM | 단일 테넌트 가상 머신 |Y | Flex 등의 모든 유료 플랜은 단일 테넌트 VM 또는 베어메탈입니다. |
|  | ICIAE |Y | IBM 지원 센터에서 요청. ICIAE가 기존 서비스 환경을 요청하는 경우 IBM 지원 센터에서 사용자 데이터를 ICIAE 환경으로 마이그레이션해야 합니다. |
|  | VPN |Y | IBM 지원 센터에서 요청 |
|  | 온디스크 암호화 |Y | -  |
|  | SSL/TLS 연결 |Y | -  |
|  | IP 화이트리스팅 | 일부 | Db2 사용자 레벨에서 사용 가능. 네트워크 레벨의 경우 ICIAE 또는 이와 유사한 항목을 고려하십시오.  |
|  | 키 보호(고유 키 가져오기) | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS/상호연결된 서비스 | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | 최대 동시 연결 한계: **무료 플랜** |Y | 최대: 5개의 연결  |
|  | 최대 동시 연결 한계: **유료 플랜** | N | 무제한 연결  |
|  |  |  |  |
| 가격 & 구매 | BYOL 할인 |Y | [공지사항 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | IBM Cloud에서 사용 가능 |Y | 구독 및 종량과금제 모두 |
|  | 소프트웨어 견적 주문을 통해 사용 가능 |Y | Flex 등의 모든 플랜. [파트 & 세부사항 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  |HDMP(Hybrid Data Management Platform)에서 사용 가능 |Y | Flex 플랜만 해당합니다. [HDMP에 관한 세부사항 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:new_window}|
|  | 일별 비용 청구 |Y | Flex 플랜에 대한 비용 청구는 일별 피크 사용량을 기반으로 합니다. 예를 들어 하루 한 시간 동안 2~8개의 코어를 스케일링하는 경우 해당 일에 대해서만 코어 8개의 비용을 청구하고 그 달의 다른 모든 날에 대해서는 코어 2개의 비용을 청구합니다. |
|  | 시간별 비용 청구 | [로드맵 내 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | 기본 가격 메트릭 | 월별 | 가격이 월 단위로 책정됩니다(예: 월별 $189 USD). 비례 배분된 월별 가격은 서비스가 종료된 달에 활성화된 서비스 일 수를 기반으로 합니다. [예](/docs/services/Db2onCloud/plans_pricing.html) |
|  |  |  |  |
| 배치 & 스케일링 기간 | 댈러스 | **배치**: < 5분. **스케일**: < 45분. | Flex 플랜만 해당, 재고에 따라 다름 |
| | 기타 미국 남부 | **배치**: 1일. **스케일**: 8시간. | 일부 지역은 다른 지역보다 짧음 |
| | 프랑크푸르트 & 런던 | **배치**: < 5분. **스케일**: 2시간. | Flex 플랜만 해당, 재고에 따라 다름 |
| | 기타 EU | **배치**: 3~5일. **스케일**: 1~2일. | 일부 지역은 다른 지역보다 짧음 |
| | 시드니 | **배치**: < 1시간. **스케일**: 2시간. | Flex 플랜만 해당, 재고에 따라 다름 |
| | 기타 AP | **배치**: 3~5일. **스케일**: 3~5일. | 일부 지역은 다른 지역보다 짧음. AP에서는 볼륨이 작을수록 인프라 프로비저닝 시간이 느려집니다. |
{: caption="표 1. Db2 on Cloud에서 지원되는 기능 및 스펙" caption-side="top"}

