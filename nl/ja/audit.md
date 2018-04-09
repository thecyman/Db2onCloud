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

# 監査
{: #audit}

{{site.data.keyword.Db2_on_Cloud_short}} データベースのアクティビティーを監査する方法を次に示します。

* [CHANGE HISTORY (変更履歴) イベント・モニター ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [タイム・トラベル照会![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

CHANGE HISTORY (変更履歴) イベント・モニターを作成することによって、イベント・モニター・テーブルに照会を実行し、データベース内で誰によって何が行われたかを判別できます。 

タイム・トラベル照会を使用すると、データに対するすべての変更を簡単に保存し、選択した時点を基にして、それよりも古いデータを照会することもできます。この監査方式を使用するには、まず、タイム・トラベル照会をサポートするようにテーブルを設定してください。

これらの監査方式について詳しくは、[変更を監査または追跡する方法![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}を参照してください。
