---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# 审计、日志记录和监视
{: #aud-log-mon}

## 审计
{: #auditing}

您可以创建数据库审计策略来审计数据库中审计事件表内存储的各类事件。有关更多信息，请参阅 [Audit policy guidelines ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}。

此外，还可以使用以下方法来审计和跟踪数据库更改：
* 通过创建 `CHANGE HISTORY` 事件监视器，您可以查询事件监视器表以确定数据库中已完成的操作以及操作人员。有关更多信息，请参阅 [`CHANGE HISTORY` 事件监视器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}。
* Time Travel Query 可轻松存储所有数据更改，甚至可基于选中的时间点查询旧数据。要使用此审计方法，请确保首先设置表以支持 Time Travel Query。有关更多信息，请参阅 [Time Travel Query ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}

有关审计和跟踪数据库更改的详细信息，请参阅[如何审计或跟踪更改？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}。

## 日志记录和监视
{: #log_mon}

日志记录和监视是服务的一部分，但不直接公开给最终用户。通常，由 IBM 操作人员使用基础架构来解决问题。  

有关 Activity Tracker 的可用性信息，请参阅[路线图 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://ibm.biz/db2oncloud-roadmap){:new_window}。

您可以使用 Db2 命令行客户机（例如 CLPPlus）进行连接以访问详细信息和诊断。

### 基本概述：
{: #basic_overview}

有 2 种基本类型的检查。外部运行状况/正常运行时间检查和基于度量值的监视。IBM 会监视数百个度量值，并存储这些度量值的历史记录。根据这些度量值来生成警报。将这些警报发送给 IBM 操作人员，以确保他们能够及时查看和解决警报。此外，IBM 还会发送归档的操作系统和诊断日志，以便进行快速诊断。{{site.data.keyword.Db2_on_Cloud_short}} 符合 GDPR，如果需要，可以通过 IBM EU Cloud 选项来获得更高级别的 GDPR 遵从性。


