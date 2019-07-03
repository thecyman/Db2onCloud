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

# 功能部件和规范
{: #fs}

此处提供 {{site.data.keyword.Db2_on_Cloud_long}} 功能部件和规范的摘要，以便于您参考。
{: shortdesc}

| 类别 | 功能部件 | 是否受支持？ | 注释 |
|----------|---------|------------|----------|
| 通用 | Db2 AESE | 是 | Db2 V11.1.3.3 |
|  | 备用读取 | 是 | 仅限非现场 DR 节点 |
|  | 自动滚动更新 | 是 | 带 HA 套餐 |
|  | 数据中心位置选项 | 是 | [位置 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-locations){:new_window}。另请参见：部署和扩展持续时间。|
|  | 内存中 BLU | 是 | 缺省值为行，为 BLU 指定 `CREATE TABLE..AS COL` |
|  | Activity Tracker | [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | 提供根目录访问权 | 否 | 如果需要根目录访问权，请使用 Db2 托管 |
|  |  |  |  |
| 高可用性和复制 | 非现场 DR | 是 | - |
|  | 高可用性（1 个区域 2 个节点） | 是 | 99.99% 正常运行时间 SLA |
|  | 不同区域在同一个数据中心内 | [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | **注**：非现场 HADR 可用 |
|  | 变更数据捕获 (CDC) | 是 | - |
|  | 用作来自内部部署的 HADR | 否 | 请使用 CDC。有关其他信息，请参阅[如何将数据从 Db2 迁移或同步到 Db2 on Cloud？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | 自主故障转移 - HA | 是 | - |
|  | 自主故障转移 - 非现场 DR | 否 | 请使用按钮或 API |
|  | IP 随故障转移移动 | 是 | 仅限本地 HA；不支持非现场 HADR |
|  | RPO：高可用性 | 0 秒 | HA 是同步的 |
|  | RTO：高可用性 | 通常，0-10 分钟 | 使用重试代码时，Db2 ACR 的速度会变慢 |
|  | RPO：非现场节点 HADR | 通常，< 15 秒 | 非现场 DR 是异步的 |
|  | RTO：非现场节点 HADR | < 3 分钟 | 必须通过控制台按钮或 API 启动 |
|  |  |  |  |
| 系统配置 | 最大 RAM 和核心数 | 1 TB RAM，48 个核心 | 适用于 Precise Performance XL 套餐 |
|  | 最大存储 | 11 TB | 适用于 Precise Performance XL 套餐。用于存储数据和日志的磁盘。|
|  | Flex：基本套餐 | 4 GB RAM，1 个核心，2 GB 磁盘 | - |
|  | Flex：最大 RAM 和核心数 | 128 GB RAM，32 个核心 | 需要更高的规格？使用 Precise Performance 套餐或联系 IBM 支持人员。|
|  | Flex：最大存储 | 4 TB | 用于存储数据和日志的磁盘。需要更高的规格？使用 Precise Performance 套餐或联系 IBM 支持人员。|
|  |  |  |  |
| 维护策略和 SLA | 高可用性套餐 | 99.99% | - |
|  | 单服务器套餐 | 99.5% | - |
|  | 非现场 DR 节点 | 99.5% | 必须使用其他本地 HA 才能达到 99.99% |
|  |维护策略| 是 | [阅读详细信息 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| 安全合规性 | HIPAA 就绪 | 是 | 包括 Flex 在内的所有付费套餐。必须向 IBM 支持人员请求 HIPAA 模式。|
|  | HITRUST  | [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | 目前可将 Db2 托管用于 HITRUST |
|  | 国际标准化组织 (ISO)  | 是 | ISO 27001、27002、27017、27018 |
|  | 服务组织控制 (SOC) | 是 | SOC 2 第 2 类 |
|  | GDPR | 是 | - |
|  | 欧盟云 | 是 | 请使用法兰克福区域。在欧盟范围内实地提供支持。|
|  | 合规性完整列表 | 是 | [安全合规性 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| 备份和复原 | 每日备份 | 是 | 14 天的每日备份 |
|  | 时间点自服务恢复 | 2018 年 11 月 15 日起可用 | [时间点复原](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
|  | 保留非现场备份 | 根据请求 | 自 2018 年 12 月 1 日起，缺省值为非现场  |
|  | 备份最长保留 10 年 | 根据请求 | 自 2018 年 12 月 1 日起。需要支持凭单。|
|  | 无需复原即可查询旧数据 | 是 | 必须设置 [Time Travel Query ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| 联网、安全性和 VM | 单租户虚拟机 | 是 | 包括 Flex 在内的所有付费套餐都是单租户 VM 或裸机。|
|  | ICIAE | 是 | 向 IBM 支持人员请求。如果为现有服务环境请求 ICIAE，那么必须由 IBM 支持人员将数据迁移到 ICIAE 环境。|
|  | VPN | 是 | 向 IBM 支持人员请求 |
|  | 磁盘上加密 | 是 | -  |
|  | SSL/TLS 连接 | 是 | -  |
|  | IP 列入白名单 | 部分 | 在 Db2 用户级别可用。对于网络级别，请考虑使用 ICIAE 或类似功能部件。|
|  | Key Protect（自带密钥）| [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / 互连服务 | [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | 最大并发连接限制：**免费套餐** | 是 | 最大：5 个连接  |
|  | 最大并发连接限制：**付费套餐** | 否 | 无限数量的连接  |
|  |  |  |  |
| 定价和采购 | BYOL 折扣 | 是 | [声明 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | 在 IBM Cloud 上提供 | 是 | 预订和现收现付均可 |
|  | 通过软件报价单提供 | 是 | 包括 Flex 在内的所有套餐。[部件和详细信息 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | 在 Hybrid Data Management Platform (HDMP) 上提供 | 是 | 仅限 Flex 套餐。[有关 HDMP 的详细信息 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:new_window}|
|  | 每日计费 | 是 | Flex 套餐的计费依据是每天使用量峰值。例如，一天中有一个小时从 2 个核心扩展到了 8 个核心，那么只有那一天会按 8 个核心计费，该月的其他每天都按 2 个核心计费。|
|  | 每小时计费 | [在路线图中 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | 主要定价指标 | 每月 | 按月定价（例如，每月 $189 美元）。每月按比例价格的依据是在服务终止的月份内激活服务的天数。[示例](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
|  |  |  |  |
| 部署和扩展持续时间 | 达拉斯 | **部署**：< 5 分钟。**扩展**：< 45 分钟。| 仅限 Flex 套餐，具体取决于库存 |
| | 其他美国南部 | **部署**：1 天。**扩展**：8 小时。| 在某些位置时间会比其他位置短一些 |
| | 法兰克福和伦敦 | **部署**：< 5 分钟。**扩展**：2 小时。| 仅限 Flex 套餐，具体取决于库存 |
| | 其他欧盟 | **部署**：3-5 天。**扩展**：1-2 天。| 在某些位置时间会比其他位置短一些 |
| | 悉尼 | **部署**：< 1 小时。**扩展**：2 小时。| 仅限 Flex 套餐，具体取决于库存 |
| | 其他亚太地区 | **部署**：3-5 天。**扩展**：3-5 天。| 在某些位置时间会比其他位置短一些。在亚太地区，如果容量较小，基础架构供应时间就会较慢。|
{: caption="表 1. Db2 on Cloud 中支持的功能部件和规范" caption-side="top"}

