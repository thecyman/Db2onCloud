---

copyright:
  years: 2014, 2019
lastupdated: "2019-06-12"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# フィーチャーおよび仕様
{: #fs}

{{site.data.keyword.Db2_on_Cloud_long}} のフィーチャーおよび仕様の要約を参照用に以下に示します。
{: shortdesc}


| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| Db2 AESE | Y | Db2 v11.1.3.3 |
| Read on Standby | Y | オフサイト DR ノードのみ |
| 自動ローリング更新 | Y | HA プラン |
| データ・センターの場所のオプション | Y | [場所](https://ibm.biz/db2oncloud-locations){:external}。『デプロイおよびスケーリングの所要時間』も参照。 |
| BLU インメモリー | Y | デフォルトは行です。BLU を使用するには `CREATE TABLE..AS COL` を指定してください |
| Activity Tracker | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| root アクセス権限の提供 | N | root アクセス権限が必要な場合は Db2 Hosted を使用してください |
{: class="simple-tab-table"}
{: caption="表 1. 一般" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| オフサイト DR | Y | - |
| 高可用性 (1 つのゾーンに 2 つのノード) | Y | 99.99% アップタイム SLA |
| 同じデータ・センター内の異なるゾーン | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | **注**: オフサイト HADR を使用可能 |
| Change Data Capture (CDC) | Y | - |
| オンプレミスから HADR として使用 | N | CDC を使用してください。 詳しくは、[How can I migrate or sync data from Db2 to Db2 on Cloud?](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external} を参照してください |
| 自律型フェイルオーバー - HA | Y | - |
| 自律型フェイルオーバー - オフサイト DR | N | ボタンまたは API を使用してください |
| フェイルオーバーに伴う IP 移動 | Y | ローカル HA のみ。オフサイト HADR ではなし |
| RPO: 高可用性 | 0 秒 | HA は同期 |
| RTO: 高可用性 | 通常 0 から 10 分 | 再試行コードを使用した場合は Db2 ACR の場合の遅さで出現 |
| RPO: オフサイト・ノード HADR | 通常 < 15 秒 | オフサイト DR は非同期 |
| RTO: オフサイト・ノード HADR | < 3 分 | コンソール・ボタンまたは API を使用して開始する必要があります |
{: class="simple-tab-table"}
{: caption="表 2. 高可用性およびレプリケーション" caption-side="top"}
{: #simpletabtable2}
{: tab-title="High availability & replication"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| 最大 RAM およびコア数 | 1 TB RAM、48 コア | Precise Performance XL プランに適用されます |
| 最大ストレージ | 11 TB | Precise Performance XL プランに適用されます。 データとログの両方のためのディスク。 |
| Flex: 基本プラン | 4 GB RAM、1 コア、2 GB ディスク | - |
| Flex: 最大 RAM およびコア数 | 128 GB RAM、32 コア | より高い仕様が必要ですか? Precise Performance プランを使用するか IBM サポートにお問い合わせください。 |
| Flex: 最大ストレージ | 4 TB | データとログの両方のためのディスク。 より高い仕様が必要ですか? Precise Performance プランを使用するか IBM サポートにお問い合わせください。 |
{: class="simple-tab-table"}
{: caption="表 3. システム構成" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| 高可用性プラン | 99.99% | - |
| 単一サーバー・プラン | 99.5% | - |
| オフサイト DR ノード | 99.5% | 99.99 % を達成するには、追加のローカル HA を使用する必要があります。 |
| 保守ポリシー | Y | [詳細を読む](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="表 4. 保守ポリシーおよび SLA" caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies & SLAs"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| HIPAA 準拠 | Y | Flex も含めてすべての有料プラン。 IBM サポートに HIPAA モードを要求する必要があります。 |
| HITRUST  | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | 現在は HITRUST 用に Db2 Hosted を使用できます |
| 国際標準化機構 (ISO)  | Y | ISO 27001、27002、27017、および 27018 |
| Service Organization Controls (SOC) | Y | SOC 2 タイプ 2 |
| GDPR | Y | - |
| EU クラウド | Y | フランクフルト地域を使用してください。 サポートは物理的に EU で提供されます。 |
| コンプライアンスの完全リスト | Y | [セキュリティー・コンプライアンス](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:external} |
{: class="simple-tab-table"}
{: caption="表 5. セキュリティー・コンプライアンス" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| 日次バックアップ | Y | 14 日間の日次バックアップ |
| ポイント・イン・タイム・セルフ・サービス・リカバリー | 2018 年 11 月 15 日から使用可能 | [ポイント・イン・タイム・リストア](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| オフサイトでのバックアップの保持 | 要求時 | 2018 年 12 月 1 日時点ではオフサイトがデフォルトです  |
| 最長 10 年までバックアップを保持 | 要求時 | 2018 年 12 月 1 日時点ではサポート・チケットが必要です |
| リストアせずに古いデータを照会 | Y | [タイム・トラベル照会](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external}のセットアップが必要です |
{: class="simple-tab-table"}
{: caption="表 6. バックアップとリストア" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup & restore"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| シングル・テナント仮想マシン | Y | すべての有料プラン (Flex も含む) は、シングル・テナント仮想マシンまたはベアメタルです。 |
| ICIAE | Y | IBM サポートに依頼。 既存のサービス環境に対して ICIAE が要求される場合、IBM サポートによってお客様のデータがお客様の ICIAE 環境にマイグレーションされる必要があります。 |
| VPN | Y | IBM サポートに依頼 |
| オンディスク暗号化 | Y | -  |
| SSL/TLS 接続 | Y | -  |
| IP ホワイトリスティング | 一部 | Db2 ユーザー・レベルで使用可能。 ネットワーク・レベル用には ICIAE などを検討してください。  |
| 鍵の保護 (持ち込み鍵) | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| MIS / 相互接続サービス | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| 最大同時接続限界値: **無料プラン** | Y | 最大: 5 接続  |
| 最大同時接続限界値: **有料プラン** | N | 接続数は無制限  |
{: class="simple-tab-table"}
{: caption="表 7. ネットワーキング、セキュリティー、および VM" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, & VMs"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| BYOL 割引 | Y | [発表](https://ibm.biz/db2oncloud-byol){:external} |
| IBM Cloud 上で使用可能 | Y | サブスクリプションと従量課金 (PAYG) の両方 |
| ソフトウェア見積もりオーダーで入手可能 | Y | Flex も含めてすべてのプラン。 [パーツおよび詳細](https://ibm.biz/db2oncloud-parts-public){:external}|
| Hybrid Data Management Platform (HDMP) 上で使用可能 | Y | Flex プランのみ。 [HDMP についての詳細](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| 日次請求 | Y | Flex プランの請求処理は、ピーク日次使用量に基づきます。 例えば、ある 1 日のある 1 時間だけ 2 個のコアから 8 個のコアに拡大する場合、その日についてのみ 8 個のコアに関して請求され、その月の他のすべての日については 2 個のコアに関して請求されます。 |
| 毎時請求 | [ロードマップ内](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
| メイン料金算定基準 | 月次 | 料金は月単位で示されます (例: 月当たり 189 ドル)。 月次料金の日割り計算は、サービスが終了した月のうちサービスがアクティブだった日数に基づきます。 [例](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="表 8. 料金および購入" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| フィーチャー | サポートの有無 | コメント |
|---------|------------|----------|
| ダラス | **デプロイ**: < 5 分。 **スケーリング**: < 45 分。 | Flex プランのみ (インベントリーによる) |
| その他の米国南部 | **デプロイ**: 1 日。 **スケーリング**: 8 時間。 | 他の場所より短い場所があります |
| フランクフルトおよびロンドン | **デプロイ**: < 5 分。 **スケーリング**: 2 時間。 | Flex プランのみ (インベントリーによる) |
| その他の EU | **デプロイ**: 3 日から 5 日。 **スケーリング**: 1 日から 2 日。 | 他の場所より短い場所があります |
| シドニー | **デプロイ**: < 1 時間。 **スケーリング**: 2 時間。 | Flex プランのみ (インベントリーによる) |
| その他の AP | **デプロイ**: 3 日から 5 日。 **スケーリング**: 3 日から 5 日。 | 他の場所より短い場所があります。 AP でのボリュームが小さいと、インフラストラクチャーのプロビジョニング時間が遅くなります。 |
{: class="simple-tab-table"}
{: caption="表 9. デプロイおよびスケーリングの所要時間" caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment & scaling durations"}
{: tab-group="fs"}

