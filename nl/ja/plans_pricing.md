---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-31"

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

# プランと料金
{: #plans_pricing}

## プランおよび構成
{: #plans_cfgs}

お客様の用途に合わせて構成および最適化されている {{site.data.keyword.Db2_on_Cloud_short}} プランを選択できます。
{: shortdesc}

   * Flex プラン (推奨)。RAM、ストレージ、およびコンピュートのリソースを個別に拡張可能
   * Precise Performance プラン。固定のリソースとベア・メタル・サーバーを提供
   * 各プランは、高可用性と Oracle 互換性を実現するように構成できます。

大量の分析やウェアハウジング・ワークロードに対処する必要がある場合は、[{{site.data.keyword.dashdblong}} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/db2-warehouse-on-cloud){:new_window}を検討してください。

必要な構成がカタログにない場合は、[{{site.data.keyword.IBM_notm}} 営業担当員に連絡して ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/connect/ibm/us/en/?lnk=fcw){:new_window}、他のオプションについて相談してください。

## 料金
{: #pricing}

料金は、アクティブであったサービスに対して月単位で課金されます (例えば、月当たり 189 米ドル)。 

アクティブであったサービスが月末前に終了した場合は、その月のうちサービスがアクティブの状態であった部分が月次料金に反映されます。

### 請求例
{: #examples}

以下の請求例では、月当たり 189 米ドルのプラン課金例が使用されます。

**例 1: 月次請求**

月次請求期間ごとにサービスがアクティブの状態であれば、サービスがアイドル状態であったとしても、月当たり 189 米ドルの料金が請求されます。

**例 2: 日次請求**

Flex プランの請求処理は、ピーク日次使用量に基づきます。例えば、ある 1 日のある 1 時間だけ 2 個のコアから 8 個のコアに拡大する場合、その日についてのみ 8 個のコアに関して請求され、その月の他のすべての日については 2 個のコアに関して請求されます。

**例 3: 日割り請求**

アクティブであったサービスの月額課金が月当たり 189 米ドルであり、そのサービスが月 30 日のうち 20 日間使用された後終了した場合、その使用量に対する請求は 189 米ドル x 20/30 = 126 米ドルになります。

