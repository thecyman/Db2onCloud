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

# 审计
{: #audit}

以下方法可用于审计 {{site.data.keyword.Db2_on_Cloud_short}} 数据库上的活动：

* [CHANGE HISTORY 事件监视器 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

通过创建 CHANGE HISTORY 事件监视器，您可以查询事件监视器表以确定数据库中已完成的操作以及操作人员。 

Time Travel Query 可轻松存储所有数据更改，甚至可基于选中的时间点查询旧数据。要使用此审计方法，请确保首先设置表以支持 Time Travel Query。

有关这些审计方法的更多信息，请参阅[如何审计或跟踪更改？![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.
