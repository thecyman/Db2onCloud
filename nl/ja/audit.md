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

# 監査、ロギング、およびモニタリング
{: #aud-log-mon}

## 監査
{: #auditing}

データベース内の監査イベント・テーブルに保管されるさまざまなカテゴリーのイベントを監査できるようにするためのデータベース監査ポリシーを作成できます。 詳しくは、[監査ポリシーのガイドライン ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window} を参照してください。

データベースに加えられた変更の監査と追跡は、以下の方法でも行えます。
* `CHANGE HISTORY` イベント・モニターを作成することによって、イベント・モニター・テーブルに照会を実行し、データベース内で誰によって何が行われたかを判別できます。 詳しくは、[`CHANGE HISTORY` イベント・モニター ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window} を参照してください。
* タイム・トラベル照会を使用すると、データに対するすべての変更を簡単に保存し、選択した時点を基にして、それよりも古いデータを照会することもできます。 この監査方式を使用するには、まず、タイム・トラベル照会をサポートするようにテーブルを設定してください。 詳しくは、[タイム・トラベル照会 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window} を参照してください

データベース変更の監査とトラッキングについて詳しくは、[変更を監査または追跡する方法 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window} を参照してください。

## ロギングとモニタリング
{: #log_mon}

モニタリングとロギングはサービスの一部ですが、エンド・ユーザーに直接公開されるわけではありません。 このインフラストラクチャーは、問題に対処するために IBM 運用スタッフ側で使用されます。  

Activity Tracker のアベイラビリティーについては、[ロードマップ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} を参照してください。

CLPPlus などの Db2 コマンド・ライン・クライアントと接続して、詳細な情報と診断情報にアクセスできます。

### 基本的概要
{: #basic_overview}

検査には 2 つの基本タイプがあります。 外部ヘルス/アップタイム検査とメトリック・ベースのモニタリングです。 IBM は何百ものメトリックをモニターし、それらのメトリックを履歴として保管します。 これらのメトリックの値に基づいて、アラートが生成されます。 これらのアラートは IBM 運用スタッフに送信され、アラートが表示されて対処されます。 さらに IBM は、迅速に診断するために、アーカイブされたオペレーティング・システムと診断ログも送信します。 {{site.data.keyword.Db2_on_Cloud_short}} は GDPR に準拠しており、必要な場合は、より高い GDPR 順守レベルも IBM EU Cloud オプションとして用意されています。


