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

# 고가용성(HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 고가용성 플랜은 99.99% SLA의 뛰어난 가용성이라는 특성을 가집니다. 
{: shortdesc}

표준 고가용성 플랜에서는 <!-- without a DR node -->원활한 장애 복구 및 롤링 업데이트를 제공합니다. 이는 자동 클라이언트 재라우팅(ACR) 및 포터블 IP를 사용하여 관리됩니다.

오프사이트 재해 복구 노드의 고가용성은 현재 비공개 베타에 있습니다. 비공개 베타 참여에 대해서는 IBM 담당자에게 문의하십시오. 오프사이트 DR 노드를 사용하면 선택한 오프사이트 위치에서 데이터를 실시간으로 신속하게 데이터베이스 노드와 동기화할 수 있습니다. {{site.data.keyword.Db2_on_Cloud_short}}는 비동기 모드에서 Db2 고가용성 재해 복구(HADR) 기술을 사용하여 오프사이트 DR 노드 기능을 얻게 되고, 재해 복구 노드에서 대기 중 읽기를 제공합니다.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
