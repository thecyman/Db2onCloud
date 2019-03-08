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

# 審核、記載及監視
{: #aud-log-mon}

## 審核
{: #auditing}

您可以建立資料庫審核原則，它讓您能審核儲存在您資料庫審核事件表格中的各種種類事件。如需相關資訊，請參閱 [Audit policy guidelines ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}。

您也可以使用下列方法審核且追蹤資料庫的變更：
* 藉由建立 `CHANGE HISTORY` 事件監視器，您可以查詢事件監視器表格來判斷誰在資料庫裡做了什麼。如需相關資訊，請參閱 [`CHANGE HISTORY` event monitor ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}。
* Time Travel Query 讓您能輕鬆儲存所有資料變更，甚至根據選取的時間點來查詢您的舊資料。若要使用這個審核方法，請確定您先設定表格，以支援 Time Travel Query。如需相關資訊，請參閱 [Time Travel Query ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}

如需審核及追蹤資料庫變更的相關資訊，請參閱 [How do I audit or track changes? ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}。

## 記載及監視
{: #log_mon}

監視及記載是服務的一部分，不過它並不直接公開給一般使用者。IBM 作業人員會改為使用基礎架構來解決問題。  

如需 Activity Tracker 的可用性，請參閱 [roadmap ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.biz/db2oncloud-roadmap){:new_window}。

您可以使用 Db2 指令行用戶端（例如 CLPPlus）進行連線，以存取詳細資訊及診斷程式。

### 基本觀念：
{: #basic_overview}

有 2 種基本類型的檢查。外部性能/執行時間檢查，及以度量值為基礎的監視。IBM 會監視數以百計的度量值，並儲存那些度量值作為歷程。警示會根據這些度量值的值而產生。這些警示會傳送給 IBM 作業人員，以確保看到並解決這些警示。此外，IBM 也會傳送保存的作業系統及診斷日誌以便快速進行診斷。{{site.data.keyword.Db2_on_Cloud_short}} 遵守 GDPR，且 IBM EU Cloud 選項視需要提供更高層次的 GDPR 遵循。


