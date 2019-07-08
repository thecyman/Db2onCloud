---

copyright:
  years: 2014, 2019
lastupdated: "2019-06-12"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# 特性及規格
{: #fs}

為了方便您使用，{{site.data.keyword.Db2_on_Cloud_long}} 特性與規格彙總如下。
{: shortdesc}


| 特性    | 支援？     |註解      |
|---------|------------|----------|
| Db2 AESE | 是 | Db2 11.1.3.3 版 |
| Read on Standby | 是 | 僅限於異地 DR 節點|
|自動漸進式更新 | 是 | 搭配 HA 方案 |
|資料中心位置選項 | 是 | [位置](https://ibm.biz/db2oncloud-locations){:external}。另請參閱：部署及調整持續時間。|
| 記憶體內 BLU | 是 | 預設值為列，為 BLU 指定 `CREATE TABLE..AS COL` |
| Activity Tracker | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
|提供 root 存取權| 否 | 如果需要 root 存取權，請使用 Db2 Hosted |
{: class="simple-tab-table"}
{: caption="表 1. 一般" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
|異地 DR | 是 | - |
|高可用性（1 個區域 2 個節點）| 是 | 99.99% 執行時間 SLA |
| 相同資料中心的不同區域 | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | **附註：**可以使用異地 HADR|
| 變更資料擷取 (CDC) | 是 | - |
| 用來作為來自內部部署的 HADR | 否 | 使用 CDC。如需資訊，請參閱[如何將資料從 Db2 移轉或同步到 Db2 on Cloud？](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external}|
| 自主失效接手 - HA | 是 | - |
| 自主失效接手 - 異地 DR | 否 |使用按鈕或 API |
| 使用失效接手的 IP 移動 | 是 | 僅限於本端 HA；而非異地 HADR |
| RPO：高可用性| 0 秒 | HA 同步|
| RTO：高可用性|一般為 0-10 分鐘|具有重試代碼，將出現為 Db2 ACR 緩慢 |
| RPO：異地節點 HADR | 一般為 < 15 秒|異地 DR 非同步|
| RTO：異地節點 HADR | < 3 分鐘|必須使用主控台按鈕或 API 起始|
{: class="simple-tab-table"}
{: caption="表 2. 高可用性及抄寫" caption-side="top"}
{: #simpletabtable2}
{: tab-title="High availability & replication"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
|最大 RAM 及核心數| 1 TB RAM、48 個核心|適用於精確效能 XL 方案|
|最大儲存空間| 11 TB |適用於精確效能 XL 方案。磁碟同時適用於資料及日誌。|
|彈性：基礎方案| 4 GB RAM、1 個核心、2 GB 磁碟| - |
|彈性：最大 RAM 及核心數| 128 GB RAM、32 個核心|需要更高的規格？請使用精確效能方案或與 IBM 支援中心聯絡。|
|彈性：最大儲存空間| 4 TB |磁碟同時適用於資料及日誌。需要更高的規格？請使用精確效能方案或與 IBM 支援中心聯絡。|
{: class="simple-tab-table"}
{: caption="表 3. 系統配置" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| 高可用性計劃 | 99.99% | - |
| 單一伺服器方案 | 99.5% | - |
| 異地 DR 節點 | 99.5% | 必須使用額外的本端 HA 以達到 99.99% |
|維護原則| 是 | [閱讀詳細資料](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="表 4. 維護原則及 SLA" caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies & SLAs"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| 符合 HIPAA | 是 |包括「彈性」的所有付費方案。必須向「IBM 支援中心」要求 HIPAA 模式。|
| HITRUST  | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | 現在 Db2 Hosted 可用於 HITRUST |
| 國際標準組織 (ISO)  | 是 | ISO 27001、27002、27017 及 27018 |
| 服務組織控制 (SOC) | 是 |SOC 2 類型 2|
| GDPR | 是 | - |
| 歐盟雲端 | 是 | 使用法蘭克福地區。在歐盟實際提供的支援。 |
| 規範的完整清單 | 是 | [安全規範](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:external} |
{: class="simple-tab-table"}
{: caption="表 5. 安全規範" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| 每日備份 | 是 | 14 天的每日備份 |
| 時間點自助式回復 | 2018 年 11 月 15 日推出 | [復原點還原](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| 備份保留在異地 | 在要求時 | 自 2018 12 月 1 日起，異地是預設值。 |
| 保留備份長達 10 年 | 在要求時 | 自 2018 12 月 1 日起。需要支援問題單。 |
| 查詢舊資料而不還原 | 是 |必須設定 [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} |
{: class="simple-tab-table"}
{: caption="表 6. 備份及還原" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup & restore"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| 單一承租戶虛擬機器 | 是 |包括「彈性」的所有付費方案都是單一承租戶 VM 或裸機。|
| ICIAE | 是 | 向「IBM 支援中心」要求。如果現有服務環境需要 ICIAE，「 IBM 支援中心」必須將您的資料移轉到 ICIAE 環境。 |
| VPN | 是 | 向「IBM 支援中心」要求 |
|磁碟上的加密| 是 | -  |
| SSL/TLS 連線 | 是 | -  |
| IP 白名單 | 部分 | 可在 Db2 使用者層次中使用。如果是網路層次，請考慮使用 ICIAE 或類似項目。  |
| Key Protect（自帶金鑰） | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| MIS / 交互連接服務 | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| 並行連線數上限：**免費方案** | 是 | 上限：5 個連線|
| 並行連線數上限：**付費方案** | 否 |連線數無限制|
{: class="simple-tab-table"}
{: caption="表 7. 網路、安全及 VM" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, & VMs"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| BYOL 折扣 | 是 | [公告](https://ibm.biz/db2oncloud-byol){:external} |
|可透過 IBM Cloud 取得| 是 |訂閱以及隨收隨付制|
|可透過軟體報價單取得| 是 | 包括「彈性」的所有方案。[部分及詳細資料](https://ibm.biz/db2oncloud-parts-public){:external}|
|可透過混合式資料管理平台 (HDMP) 取得 | 是 | 僅限於「彈性」方案。[HDMP 相關詳細資料](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| 按日計費 | 是 |「彈性」方案是根據每日的尖峰用量計費。比方說，如果您在某一天的一小時內從 2 個核心擴增到 8 個核心，只有當天會以 8 個核心計費，而當月的所有其他日期則以 2 個核心計費。 |
| 按小時計費 | [In roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
|主要定價標準 | 每月 | 價格是按月表示（例如，每月 $189 美元）。按比例計費的每月價格是根據終止服務當月中啟動服務的天數。 [範例](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="表 8. 定價及購買" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| 特性    | 支援？     |註解      |
|---------|------------|----------|
| 達拉斯 | **部署**：< 5 分鐘。**調整**：< 45 分鐘。 | 僅限於「彈性」方案，視庫存而定 |
| 其他美國南部位置 | **部署**：1 天。**調整**：8 小時。| 某些位置比其他位置更短 |
| 法蘭克福及倫敦 | **部署**：< 5 分鐘。**調整**：2 小時。 | 僅限於「彈性」方案，視庫存而定 |
|其他歐盟位置 | **部署**：3-5 天。**調整**：1-2 天。| 某些位置比其他位置更短 |
|雪梨| **部署**：< 1 小時。**調整**：2 小時。 | 僅限於「彈性」方案，視庫存而定 |
| 其他亞太地區位置 | **部署**：3-5 天。**調整**：3-5 天。| 某些位置比其他位置更短。亞太地區因磁區較少，導致基礎架構佈建較慢。|
{: class="simple-tab-table"}
{: caption="表 9. 部署及調整持續時間" caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment & scaling durations"}
{: tab-group="fs"}

