---

copyright:
  years: 2014, 2018
lastupdated: "2018-07-19"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# 高可用性 (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性プランは、SLA 99.99% の優れた可用性特性があります。 
{: shortdesc}

DR ノードを使用しない標準の高可用性プランは、シームレスなフェイルオーバーとローリング更新を提供します。これらは、自動クライアント・リルート (ACR) とポータブル IP を使用して管理されます。

さらに、Geo レプリケートされた災害復旧ノードを追加することもできます。このオフサイトの DR ノード・オプションを使用すると、選択したオフサイト {{site.data.keyword.Bluemix_notm}} データ・センターのデータベース・ノードにデータをリアルタイムで迅速に同期させることができます。 

[DR ノードが使用可能なデータ・センターの場所のリスト。 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} は、`ASYNC` モードの DB2 高可用性災害時リカバリー (HADR) テクノロジーを使用して、オフサイトの DR ノード機能を実現し、DR ノードに `Read on Standby` を提供します。

## Geo レプリケートされた災害復旧ノードの追加方法
{: #add_dr}

既存の {{site.data.keyword.Db2_on_Cloud_short}} ユーザーの場合:
 * オンデマンドの DR ノードを既存の {{site.data.keyword.Db2_on_Cloud_short}} インスタンスに追加できます。{{site.data.keyword.Bluemix_notm}} ダッシュボードでインスタンスをクリックすると、**「災害復旧の管理 (Manage Disaster Recovery)」**というオプションが表示されます。そこから Geo レプリケートされた災害復旧ノードを追加できます。
 * 営業担当員を通した契約で {{site.data.keyword.Db2_on_Cloud_short}} を購入し、{{site.data.keyword.Bluemix_notm}} サブスクリプションを持っていない場合は、IBM 担当員に問い合わせて、DR ノードを追加してください。

現在、{{site.data.keyword.Db2_on_Cloud_short}} ユーザーではない場合:
 * {{site.data.keyword.Bluemix_notm}} を通して {{site.data.keyword.Db2_on_Cloud_short}} を注文するか、営業担当員に問い合わせてください。
 * その後、コンソールで**「災害復旧の管理 (Manage Disaster Recovery)」**を使用して DR ノードを追加できます。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## 高可用性および災害復旧ノードの管理
{: #manage_ha_dr}

オフサイトではない標準の HA ノードの場合、フェイルオーバーは IBM によって管理されます。IBM はサーバーのヘルスをモニターし、必要に応じて、フェイルオーバーやフェイルバックを行い、ローリング更新やスケーリングなども実施して、アップタイムを可能な限り長く保つようにします。

Geo レプリケートされた災害復旧 (HADR) の場合は、コンソールで**「災害復旧の管理 (Manage Disaster Recovery)」**を使用して手動でフェイルオーバーする必要があります。また、[ここ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}で説明する API を使用してフェイルオーバーすることもできます。

## FAQ
{: #faq}

### テークオーバー後に、DB2 を使用しているアプリケーションが DR リカバリーと連動するためには、何を変更する必要がありますか? テークオーバー後、DNS 名や IP アドレスは変更されますか?

**A**: いいえ。2 つの解決可能なホスト名が与えられます。アプリが Db2 ACR (Active Connection Reroute、自動クライアント・リルート) を使用するように構成されている場合、アプリは新しい 1 次ノードにリルートされます。

Geo レプリケートされた災害復旧ノードについて詳しくは、[ここ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}をクリックしてください。
