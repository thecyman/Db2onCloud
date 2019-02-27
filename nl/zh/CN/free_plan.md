---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# 免费套餐
{: #free_plan}

{{site.data.keyword.Db2_on_Cloud_long}} 免费套餐提供了基本资源，可用于开发或了解 Db2，无需任何费用。
{: shortdesc}

免费套餐无时间限制，但用户必须每 30 天重新延长其免费套餐。

仅提供社区支持。 
 
## 体系结构
{: #architecture}

与其他 {{site.data.keyword.Db2_on_Cloud_short}} 套餐不同，{{site.data.keyword.Db2_on_Cloud_short}} 免费套餐在多租户系统上运行。Flex 和 Precise Performance 套餐在其自己的单租户虚拟机或裸机服务器上运行。
 
免费套餐允许使用一个数据库模式。

有关 {{site.data.keyword.Db2_on_Cloud_short}} 免费套餐的更多信息，请参阅[常见问题 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oc_free_plan_faq){:new_window}。

## 在北美大陆之外使用免费套餐
{: #outside_na}

对于北美大陆，目前无需信用卡也可以访问免费套餐。在北美大陆之外，客户必须向其 IBM Cloud 帐户添加信用卡，然后选择“美国南部 - 达拉斯”区域，才能查看和选择免费套餐。

免费套餐始终免费且不会向信用卡收取费用。

## 免费套餐限制
{: #fp_restrictions}

对于任务关键型或性能敏感型工作负载，强烈建议您使用企业级服务套餐，而不是免费服务套餐。
{: important}

下表显示了 {{site.data.keyword.Db2_on_Cloud_short}} 免费套餐限制：

| 类别 | 项目 | 限制 | 
|----------|------|-------------|
| 资源 | 存储空间 | 每个用户 200 MB 的存储空间 |
|  | 连接数 | 每个用户 5 个连接 |
|  | 性能 | 由于多租户系统上其他用户运行的工作负载，性能可能会出现波动 |
|  |  |
| 特性和功能 | 联合 | 不支持 |
|  | Oracle 兼容性 | 不支持 |
|  | 用户定义的扩展 (UDF) | 任何 {{site.data.keyword.Db2_on_Cloud_short}} 套餐（包括免费套餐）都不支持 |
|  | 用户管理 | 未授予用户管理权限 |
|  | 行和列访问控制 (RCAC) | 不支持 |
|  | 使用 IBM InfoSphere Data Replication 装入数据 | 不支持 |
|  |  |
| 联网环境 | IBM Cloud Integrated Analytics | 不支持 |
|  | IBM Cloud Dedicated | 不支持 |
|  |  |
| 安全合规性 | 1996 年颁布的健康保险可移植性和责任法案 (HIPAA) | 不支持。请参阅“服务描述”。|
|  | 欧盟一般数据保护条例 (GDPR) | 不支持。请参阅“服务描述”。|
|  |  |
| 帐户管理 | 重新激活 | 每 30 天需要重新激活一次。如果不重新激活，那么会在 60 天后删除免费套餐服务。|
{: caption="表 1. {{site.data.keyword.Db2_on_Cloud_short}} 免费套餐限制" caption-side="top"}


