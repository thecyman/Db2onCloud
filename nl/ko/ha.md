---

copyright:
  years: 2014, 2018
lastupdated: "2018-07-19"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# 고가용성(HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 고가용성 플랜은 99.99% SLA의 뛰어난 가용성이라는 특성을 가집니다. 
{: shortdesc}

DR 노드가 없는 표준 고가용성 플랜에서는 원활한 장애 복구 및 롤링 업데이트를 제공합니다. 이는 자동 클라이언트 재라우팅(ACR) 및 포터블 IP를 사용하여 관리됩니다.

Geo-Replicated Disaster Recovery 노드도 추가할 수 있습니다. 이 오프사이트 DR 노드 옵션을 사용하면 선택한 오프사이트 {{site.data.keyword.Bluemix_notm}} 데이터 센터에서 데이터를 실시간으로 신속하게 데이터베이스 노드와 동기화할 수 있습니다.  

[DR 노드를 사용할 수 있는 데이터 센터 위치 목록입니다. ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}}에서는 `비동기` 모드에서 DB2 고가용성 재해 복구(HADR) 기술을 사용하여 오프사이트 DR 노드 기능을 얻고 DR 노드에서 `대기 중 읽기`를 제공합니다.

## Geo-Replicated Disaster Recovery 노드 추가 방법
{: #add_dr}

기존 {{site.data.keyword.Db2_on_Cloud_short}} 사용자의 경우:
 * 기존 {{site.data.keyword.Db2_on_Cloud_short}} 인스턴스에 On-Demand DR 노드를 추가할 수 있습니다. {{site.data.keyword.Bluemix_notm}} 대시보드의 인스턴스를 클릭하면 **재해 복구 관리**라는 옵션이 표시됩니다. 여기에서 Geo-Replicated Disaster Recovery 노드를 추가할 수 있습니다.
 * 영업 담당자를 통해 계약에 있는 {{site.data.keyword.Db2_on_Cloud_short}}를 구매했으며 {{site.data.keyword.Bluemix_notm}} 구독이 없으면 IBM 담당자에게 문의하여 DR 노드를 추가하십시오.

현재 {{site.data.keyword.Db2_on_Cloud_short}} 사용자가 아닌 경우:
 * {{site.data.keyword.Bluemix_notm}}를 통해 {{site.data.keyword.Db2_on_Cloud_short}}를 주문하거나 영업 담당자에게 문의하십시오.
 * 그러면 콘솔에서 **재해 복구 관리**를 사용하여 DR 노드를 추가할 수 있습니다.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## 고가용성 및 재해 복구 노드 관리
{: #manage_ha_dr}

오프사이트가 아닌 표준 HA 노드의 경우 IBM에서 장애 복구를 관리합니다. IBM은 서버의 상태와 장애 복구를 모니터하고, 가동 시간을 최대로 유지하기 위해 필요에 따라 롤링 업데이트 및 확장을 포함한 장애 조치를 수행합니다. 

Geo-Replicated Disaster Recovery(HADR)의 경우 콘솔에서 **재해 복구 관리**를 사용하여 수동으로 장애 복구를 수행해야 합니다. 또한 [여기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}에 설명된 대로 API를 사용하여 장애 복구를 수행할 수 있습니다.

## FAQ
{: #faq}

### 인계 후 DR 복구를 위해 Db2를 사용하는 애플리케이션에 필요한 변경사항은 무엇입니까? 인계 후 DNS 이름 또는 IP 주소가 변경됩니까?

**A**: 아니오. 해석 가능한 호스트 이름이 2개 제공됩니다. 앱에서 DB2 ACR(Active Connection Reroute)을 사용하도록 구성된 경우 앱의 경로가 새 기본 노드로 재지정됩니다.

Geo-Replicated Disaster Recovery 노드에 관한 자세한 정보는 [여기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}를 클릭하십시오.
