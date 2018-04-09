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

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性套餐具备卓越可用性特征以及 99.99% SLA。
{: shortdesc}

标准高可用性套餐<!-- without a DR node -->提供无缝故障转移和滚动更新。使用自动客户机重新路由 (ACR) 和可移植 IP 进行管理。

使用非现场灾难恢复节点的高可用性当前为封闭 Beta 版。请联系您的 IBM 代表以询问如何参与封闭 Beta 测试。非现场 DR 节点使您能够实时将数据快速同步至选择的非现场位置。{{site.data.keyword.Db2_on_Cloud_short}} 以 ASYNC 方式使用 Db2 高可用性灾难恢复 (HADR) 技术来实现非现场 DR 节点功能，并在灾难恢复节点上提供 Read on Standby。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
