---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-22"

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

# 高可用性 (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性套餐具备卓越可用性特征以及 99.99% SLA。
{: shortdesc}

不含灾难恢复 (DR) 节点的标准高可用性套餐提供无缝故障转移和滚动更新。使用自动客户机重新路由 (ACR) 和可移植 IP 进行管理。

此外，您可以添加地理复制灾难恢复节点。此非现场 DR 节点选项使您能够实时将数据快速同步到所选非现场 {{site.data.keyword.Bluemix_notm}} 数据中心的数据库节点。 

[DR 节点可用的数据中心位置的列表。![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} 以 `ASYNC` 方式使用 Db2 高可用性灾难恢复 (HADR) 技术来实现非现场 DR 节点功能，并在 DR 节点上提供 `Read on Standby`。

## **巴西：补充规则 14**（适用于为巴西联邦政府供应的系统）
{: #rule_14}

目前，由于补充规定 14 的原因，Db2 on Cloud 产品的灾难恢复 (DR) 选项在巴西还不能用于联邦政府。

## 如何添加地理复制灾难恢复节点
{: #add_dr}

对于现有 {{site.data.keyword.Db2_on_Cloud_short}} 用户：
 * 可以向现有 {{site.data.keyword.Db2_on_Cloud_short}} 实例添加随需应变的 DR 节点。单击 {{site.data.keyword.Bluemix_notm}}“仪表板”中的实例后，您将看到名为**管理灾难恢复**的选项。您可以从此处添加地理复制灾难恢复节点。
 * 如果通过销售代表根据合同购买了 {{site.data.keyword.Db2_on_Cloud_short}} 但没有 {{site.data.keyword.Bluemix_notm}} 预订，请联系 IBM 代表来添加 DR 节点。

如果您当前不是 {{site.data.keyword.Db2_on_Cloud_short}} 用户：
 * 通过 {{site.data.keyword.Bluemix_notm}} 订购 {{site.data.keyword.Db2_on_Cloud_short}}，或者联系销售代表。
 * 然后，可以使用控制台中的**管理灾难恢复**来添加 DR 节点。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## 管理高可用性和灾难恢复节点
{: #manage_ha_dr}

对于不是非现场的标准 HA 节点，故障转移由 IBM 管理。IBM 会监视服务器的运行状况、执行故障转移并根据需要进行故障恢复，包括滚动更新和扩展以尽可能使正常运行时间保持在最高水平。

对于地理复制灾难恢复 (HADR)，必须使用控制台中的**管理灾难恢复**来手动执行故障转移。此外，还可以使用 API 来执行故障转移，如[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window} 所述。

## 常见问题
{: #faq}

### 对于使用 Db2 来处理接管后 DR 节点的应用程序，需要进行哪些更改？接管后 DNS 名称或 IP 地址会更改吗？

**答**：不需要进行更改，DNS 名称或 IP 地址也不会更改。将为您提供 2 个可解析的主机名。如果应用程序配置为使用 Db2 ACR（活动连接重新路由），那么应用程序将重新路由到新的主节点。

有关地理复制灾难恢复节点的更多信息，请单击[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}。
