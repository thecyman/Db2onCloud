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

# 高可用性 (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性方案具有絕佳的可用性特徵，及 99.99% SLA。
{: shortdesc}

標準高可用性方案提供無縫失效接手及漸進式更新。系統使用自動用戶端重新遞送 (ACR) 及可攜式 IP 為您管理。

異地災難回復節點的高可用性目前為封閉測試版。請與您的 IBM 業務代表聯絡，詢問參與封閉測試版的相關事宜。異地 DR 節點讓您能快速即時將資料同步化到您選擇之異地位置的資料庫節點。{{site.data.keyword.Db2_on_Cloud_short}} 使用 Db2 高可用性災難復原 (HADR) 技術的 ASYNC 模式來達到異地 DR 節點功能，並在災難回復節點上提供 Read on Standby。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
