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

# 審核
{: #audit}

以下是您可以用來在 {{site.data.keyword.Db2_on_Cloud_short}} 資料庫上審核活動的方法：

* [CHANGE HISTORY 事件監視器 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

藉由建立 CHANGE HISTORY 事件監視器，您可以查詢事件監視器表格來判斷誰在資料庫裡做了什麼。 

Time Travel Query 讓您能輕鬆儲存所有資料變更，甚至根據選取的時間點來查詢您的舊資料。若要使用這個審核方法，請確定您先設定表格，以支援 Time Travel Query。

如需這些審核方法的相關資訊，請參閱 [How do I audit or track changes? ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}。
