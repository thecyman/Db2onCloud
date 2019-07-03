---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-05"

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

# フィーチャーおよび仕様
{: #fs}

{{site.data.keyword.Db2_on_Cloud_long}} のフィーチャーおよび仕様の要約を参照用に以下に示します。
{: shortdesc}

| カテゴリー | フィーチャー | サポートの有無 | コメント |
|----------|---------|------------|----------|
| 一般 | Db2 AESE | Y | Db2 v11.1.3.3 |
|  | Read on Standby | Y | オフサイト DR ノードのみ |
|  | 自動ローリング更新 | Y | HA プラン |
|  | データ・センターの場所のオプション | Y | [場所 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-locations){:new_window}。 『デプロイおよびスケーリングの所要時間』も参照。 |
|  | BLU インメモリー | Y | デフォルトは行です。BLU を使用するには `CREATE TABLE..AS COL` を指定してください |
|  | Activity Tracker | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | root アクセス権限の提供 | N | root アクセス権限が必要な場合は Db2 Hosted を使用してください |
|  |  |  |  |
| 高可用性およびレプリケーション | オフサイト DR | Y | - |
|  | 高可用性 (1 つのゾーンに 2 つのノード) | Y | 99.99% アップタイム SLA |
|  | 同じデータ・センター内の異なるゾーン | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | **注**: オフサイト HADR を使用可能 |
|  | Change Data Capture (CDC) | Y | - |
|  | オンプレミスから HADR として使用 | N | CDC を使用してください。 詳しくは、[How can I migrate or sync data from Db2 to Db2 on Cloud? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} を参照してください。 |
|  | 自律型フェイルオーバー - HA | Y | - |
|  | 自律型フェイルオーバー - オフサイト DR | N | ボタンまたは API を使用してください |
|  | フェイルオーバーに伴う IP 移動 | Y | ローカル HA のみ。オフサイト HADR ではなし |
|  | RPO: 高可用性 | 0 秒 | HA は同期 |
|  | RTO: 高可用性 | 通常 0 から 10 分 | 再試行コードを使用した場合は Db2 ACR の場合の遅さで出現 |
|  | RPO: オフサイト・ノード HADR | 通常 < 15 秒 | オフサイト DR は非同期 |
|  | RTO: オフサイト・ノード HADR | < 3 分 | コンソール・ボタンまたは API を使用して開始する必要があります |
|  |  |  |  |
| システム構成 | 最大 RAM およびコア数 | 1 TB RAM、48 コア | Precise Performance XL プランに適用されます |
|  | 最大ストレージ | 11 TB | Precise Performance XL プランに適用されます。 データとログの両方のためのディスク。 |
|  | Flex: 基本プラン | 4 GB RAM、1 コア、2 GB ディスク | - |
|  | Flex: 最大 RAM およびコア数 | 128 GB RAM、32 コア | より高い仕様が必要ですか? Precise Performance プランを使用するか IBM サポートにお問い合わせください。 |
|  | Flex: 最大ストレージ | 4 TB | データとログの両方のためのディスク。 より高い仕様が必要ですか? Precise Performance プランを使用するか IBM サポートにお問い合わせください。 |
|  |  |  |  |
| 保守ポリシーおよび SLA | 高可用性プラン | 99.99% | - |
|  | 単一サーバー・プラン | 99.5% | - |
|  | オフサイト DR ノード | 99.5% | 99.99 % を達成するには、追加のローカル HA を使用する必要があります。 |
|  | 保守ポリシー | Y | [詳しくはこちらをご覧ください ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| セキュリティー・コンプライアンス | HIPAA 準拠 | Y | Flex も含めてすべての有料プラン。 IBM サポートに HIPAA モードを要求する必要があります。|
|  | HITRUST  | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | 現在は HITRUST 用に Db2 Hosted を使用できます |
|  | 国際標準化機構 (ISO)  | Y | ISO 27001、27002、27017、および 27018 |
|  | Service Organization Controls (SOC) | Y | SOC 2 タイプ 2 |
|  | GDPR | Y | - |
|  | EU クラウド | Y | フランクフルト地域を使用してください。 サポートは物理的に EU で提供されます。 |
|  | コンプライアンスの完全リスト | Y | [セキュリティー・コンプライアンス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| バックアップおよびリストア | 日次バックアップ | Y | 14 日間の日次バックアップ |
|  | ポイント・イン・タイム・セルフ・サービス・リカバリー | 2018 年 11 月 15 日から使用可能 | [ポイント・イン・タイム・リストア](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
|  | オフサイトでのバックアップの保持 | 要求時 | 2018 年 12 月 1 日時点ではオフサイトがデフォルトです  |
|  | 最長 10 年までバックアップを保持 | 要求時 | 2018 年 12 月 1 日時点ではサポート・チケットが必要です |
|  | リストアせずに古いデータを照会 | Y | [タイム・トラベル照会 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} のセットアップが必要です |
|  |  |  |  |
| ネットワーキング、セキュリティー、および VM | シングル・テナント仮想マシン | Y | すべての有料プラン (Flex も含む) は、シングル・テナント仮想マシンまたはベアメタルです。 |
|  | ICIAE | Y | IBM サポートに依頼。 既存のサービス環境に対して ICIAE が要求される場合、IBM サポートによってお客様のデータがお客様の ICIAE 環境にマイグレーションされる必要があります。 |
|  | VPN | Y | IBM サポートに依頼 |
|  | オンディスク暗号化 | Y | -  |
|  | SSL/TLS 接続 | Y | -  |
|  | IP ホワイトリスティング | 一部 | Db2 ユーザー・レベルで使用可能。 ネットワーク・レベル用には ICIAE などを検討してください。  |
|  | 鍵の保護 (持ち込み鍵) | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / 相互接続サービス | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | 最大同時接続限界値: **無料プラン** | Y | 最大: 5 接続  |
|  | 最大同時接続限界値: **有料プラン** | N | 接続数は無制限  |
|  |  |  |  |
| 料金および購入 | BYOL 割引 | Y | [発表 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | IBM Cloud 上で使用可能 | Y | サブスクリプションと従量課金 (PAYG) の両方 |
|  | ソフトウェア見積もりオーダーで入手可能 | Y | Flex も含めてすべてのプラン。 [パーツおよび詳細 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Hybrid Data Management Platform (HDMP) 上で使用可能 | Y | Flex プランのみ。 [HDMP についての詳細 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:new_window}|
|  | 日次請求 | Y | Flex プランの請求処理は、ピーク日次使用量に基づきます。 例えば、ある 1 日のある 1 時間だけ 2 個のコアから 8 個のコアに拡大する場合、その日についてのみ 8 個のコアに関して請求され、その月の他のすべての日については 2 個のコアに関して請求されます。 |
|  | 毎時請求 | [ロードマップにあり ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | メイン料金算定基準 | 月次 | 料金は月単位で示されます (例: 月当たり 189 ドル)。 月次料金の日割り計算は、サービスが終了した月のうちサービスがアクティブだった日数に基づきます。 [例](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
|  |  |  |  |
| デプロイおよびスケーリングの所要時間 | ダラス | **デプロイ**: < 5 分。 **スケーリング**: < 45 分。 | Flex プランのみ (インベントリーによる) |
| | その他の米国南部 | **デプロイ**: 1 日。 **スケーリング**: 8 時間。 | 他の場所より短い場所があります |
| | フランクフルトおよびロンドン | **デプロイ**: < 5 分。 **スケーリング**: 2 時間。 | Flex プランのみ (インベントリーによる) |
| | その他の EU | **デプロイ**: 3 日から 5 日。 **スケーリング**: 1 日から 2 日。 | 他の場所より短い場所があります |
| | シドニー | **デプロイ**: < 1 時間。 **スケーリング**: 2 時間。 | Flex プランのみ (インベントリーによる) |
| | その他の AP | **デプロイ**: 3 日から 5 日。 **スケーリング**: 3 日から 5 日。 | 他の場所より短い場所があります。 AP でのボリュームが小さいと、インフラストラクチャーのプロビジョニング時間が遅くなります。 |
{: caption="表 1. Db2 on Cloud でサポートされるフィーチャーおよび仕様" caption-side="top"}

