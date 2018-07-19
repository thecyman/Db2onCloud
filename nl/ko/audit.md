---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-14"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# 감사
{: #audit}

다음은 {{site.data.keyword.Db2_on_Cloud_short}} 데이터베이스에서 활동을 감사하는 데 사용할 수 있는 방법입니다.

* [CHANGE HISTORY 이벤트 모니터 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [시간 이동 조회 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

CHANGE HISTORY 이벤트 모니터를 작성하면 이벤트 모니터 테이블을 조회하여 데이터베이스 내에서 수행한 작업 및 수행한 사용자를 판별할 수 있습니다. 

시간 이동 조회를 사용하면 쉽게 데이터의 모든 변경사항을 저장하고 선택한 시점을 기준으로 이전 데이터를 조회할 수 있습니다. 이 감사 방법을 사용하려면 처음에 시간 이동 조회를 지원하도록 테이블을 설정하십시오.

이러한 감사 방법에 대한 자세한 정보는 [변경사항 감사 또는 추적 방법 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}을 참조하십시오.
