---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-22"

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

# 高可用性 (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性方案具有絕佳的可用性特徵，及 99.99% SLA。
{: shortdesc}

沒有災難回復 (DR) 節點的標準高可用性方案提供無縫失效接手及漸進式更新。系統使用自動用戶端重新遞送 (ACR) 及可攜式 IP 為您管理。

此外，您可以新增「異地抄寫災難回復節點」。這個異地 DR 節點選項讓您能快速即時將資料同步化到您選擇之異地 {{site.data.keyword.Bluemix_notm}} 資料中心的資料庫節點。 

[提供 DR 節點的資料中心位置清單。![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} 使用 Db2 高可用性災難復原 (HADR) 技術的 `ASYNC` 模式來達到異地 DR 節點功能，並在 DR 節點上提供 `Read on Standby`。

## **巴西：增補規則 14**（適用於為巴西聯邦政府佈建的系統）
{: #rule_14}

目前，由於增補規則 14 之故，巴西的聯邦政府無法使用 Db2 on Cloud 供應項目的災難回復 (DR) 選項。

## 如何新增異地抄寫災難回復節點
{: #add_dr}

對於現有 {{site.data.keyword.Db2_on_Cloud_short}} 使用者：
 * 您可以將隨需應變的 DR 節點新增至現有 {{site.data.keyword.Db2_on_Cloud_short}} 實例。在 {{site.data.keyword.Bluemix_notm}} 儀表板按一下您的實例之後，您會看到一個稱為**管理災難回復**的選項。您可以從該處新增「異地抄寫災難回復節點」。
 * 如果透過業務代表購買 {{site.data.keyword.Db2_on_Cloud_short}} 合約，而沒有 {{site.data.keyword.Bluemix_notm}} 訂閱，請與您的 IBM 業務代表聯絡以便新增 DR 節點。

如果您目前不是 {{site.data.keyword.Db2_on_Cloud_short}} 使用者，請：
 * 透過 {{site.data.keyword.Bluemix_notm}} 訂購 {{site.data.keyword.Db2_on_Cloud_short}}，或洽業務代表。
 * 然後便可以在主控台使用**管理災難回復**新增 DR 節點。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## 管理高可用性及災難回復節點
{: #manage_ha_dr}

對於非異地的標準 HA 節點，失效接手是由 IBM 為您管理。IBM 會監視您伺服器的性能、失效接手，並視需要失效回復，包括漸進式更新以及擴充，以便儘可能維持高執行時間。

對於異地抄寫災難回復 (HADR)，您必須在主控台使用**管理災難回復**手動失效接手。此外，您可以使用 API 進行失效接手，如[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window} 所述。

## 常見問題
{: #faq}

### 使用 Db2 的應用程式在接管之後，若要使用 DR 節點，需要做什麼變更？DNS 名稱或 IP 位址會在接管之後變更嗎？

**答**：不會。您會得到 2 個可解析的主機名稱。如果您的應用程式已配置為使用 Db2 ACR（作用中連線重新遞送），則應用程式會重新遞送到新的主要節點。

如需異地抄寫災難回復節點的相關資訊，請按一下[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}。
