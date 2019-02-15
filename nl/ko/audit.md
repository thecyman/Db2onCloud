---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# 감사, 로깅 및 모니터링
{: #aud-log-mon}

## 감사
{: #auditing}

데이터베이스의 감사 이벤트 테이블에 저장된 다양한 이벤트 카테고리를 감사하는 기능을 제공하는 데이터베이스 감사 정책을 작성할 수 있습니다. 자세한 정보는 [감사 정책 가이드라인 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}을 참조하십시오.

또한 다음과 같은 방법을 사용하여 데이터베이스의 변경사항을 감사하고 추적할 수 있습니다.
* `CHANGE HISTORY` 이벤트 모니터를 작성하면 이벤트 모니터 테이블을 조회하여 데이터베이스 내에서 수행한 작업 및 수행한 사용자를 판별할 수 있습니다. 자세한 정보는 [`CHANGE HISTORY` 이벤트 모니터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}를 참조하십시오.
* Time Travel Query를 사용하면 쉽게 데이터의 모든 변경사항을 저장하고 선택한 시점을 기준으로 이전 데이터를 조회할 수 있습니다. 이 감사 방법을 사용하려면 처음에 Time Travel Query를 지원하도록 테이블을 설정하십시오. 자세한 정보는 [Time Travel Query ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}를 참조하십시오.

데이터베이스 변경사항 감사 및 추적에 관한 자세한 정보는 [변경사항을 감사하거나 추적하는 방법 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}을 참조하십시오.

## 로깅 및 모니터링
{: #log_mon}

모니터링과 로깅은 서비스의 일부이지만 일반 사용자에게 직접 노출되지 않습니다. IBM 운영 직원은 인프라를 사용하여 문제를 처리합니다.  

활동 트래커의 가용성은 [로드맵 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://ibm.biz/db2oncloud-roadmap){:new_window}을 참조하십시오.

자세한 정보와 진단에 액세스하기 위해 CLPPlus와 같은 Db2 명령행 클라이언트를 사용하여 연결할 수 있습니다.

### 기본 개요:
{: #overview}

검사의 기본 유형은 두 가지가 있습니다. 즉, 외부 상태/가동 시간 검사 및 메트릭 기반 모니터링입니다. IBM에서는 수백 개의 메트릭을 모니터하고 해당 메트릭을 히스토리별로 저장합니다. 해당 메트릭 값을 기반으로 경보가 생성됩니다. 경보를 보고 처리할 수 있도록 이 경보는 IBM 운영 직원에게 전송됩니다. 또한 IBM에서는 신속한 진단을 위해 아카이브된 운영 체제와 진단 로그를 전송합니다. {{site.data.keyword.Db2_on_Cloud_short}}는 GDPR을 준수하고 필요한 경우 IBM EU Cloud 옵션을 통해 더 높은 수준으로 GDPR을 준수할 수 있습니다.
