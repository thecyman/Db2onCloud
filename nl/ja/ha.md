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

{{site.data.keyword.Db2_on_Cloud_short}} 高可用性プランは、SLA 99.99% の優れた可用性特性があります。
{: shortdesc}

標準の高可用性プランは、シームレスなフェイルオーバーとローリング更新<!-- without a DR node -->を提供します。これらは、自動クライアント・リルート (ACR) とポータブル IP を使用して管理されます。

オフサイトの災害復旧ノードを使用する高可用性は現在、クローズド・ベータです。IBM 担当員に連絡して、クローズド・ベータへの参加についてお問い合わせください。オフサイトの DR ノードを使用すると、希望するオフサイトの場所にあるデータベース・ノードにデータをリアルタイムで迅速に同期させることができます。{{site.data.keyword.Db2_on_Cloud_short}} は、非同期モードの DB2 高可用性災害時リカバリー (HADR) テクノロジーを使用して、オフサイトの DR ノード機能を実現し、災害復旧ノード上のスタンバイを読み取ります。
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
