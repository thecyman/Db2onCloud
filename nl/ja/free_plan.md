---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# 無料プラン
{: #free_plan}

{{site.data.keyword.Db2_on_Cloud_long}} 無料プランでは、Db2 の開発や学習を行える基本的なリソースが無料で提供されます。
{: shortdesc}

無料プランに時間制限はありませんが、ユーザーは 30 日ごとに無料プランを再延長する必要があります。

コミュニティーのサポートのみ利用できます。 
 
## アーキテクチャー
{: #architecture}

他の {{site.data.keyword.Db2_on_Cloud_short}} プランとは異なり、{{site.data.keyword.Db2_on_Cloud_short}} 無料プランはマルチテナント・システム上で実行されます。Flex プランと Precise Performance プランは、独自のシングル・テナント仮想マシンまたはベア・メタル・サーバー上で実行されます。
 
無料プランでは、1 つのデータベース・スキーマを使用できます。

{{site.data.keyword.Db2_on_Cloud_short}} 無料プランについて詳しくは、[FAQ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://ibm.biz/db2oc_free_plan_faq){:new_window} を参照してください。

## 北アメリカ大陸以外での無料プランの使用
{: #outside_na}

北アメリカ大陸では現在、クレジット・カードなしで無料プランをご利用いただけます。北アメリカ大陸以外では、無料プランを選択肢として表示するためには、IBM Cloud アカウントにクレジット・カードを追加し、「米国南部 - ダラス」地域を選択する必要があります。

無料プランは常に無料で提供され、お客様のクレジット・カードに課金されることはありません。

## 無料プランの制約事項
{: #fp_restrictions}

基幹業務のワークロードやパフォーマンスに依存するワークロードには、無料サービス・プランではなく、エンタープライズ・レベルのサービス・プランを使用することを強くお勧めします。
{: important}

以下は、{{site.data.keyword.Db2_on_Cloud_short}} 無料プランの制約事項の表です。

| カテゴリー | 項目 | 制約 | 
|----------|------|-------------|
| リソース | ストレージ | ユーザー当たり 200 MB のストレージ |
|  | 接続数 | ユーザー当たり 5 接続 |
|  | パフォーマンス | マルチテナント・システム上の他のユーザーによって実行されるワークロードが原因でパフォーマンスが変動する可能性がある |
|  |  |
| フィーチャーおよび機能 | フェデレーション | サポートされない |
|  | Oracle 互換性 | サポートされない |
|  | ユーザー定義拡張 (UDF) | 無料プランを含め、どの {{site.data.keyword.Db2_on_Cloud_short}} プランでもサポートされない |
|  | ユーザー管理 | ユーザーに管理権限が与えられない |
|  | 行/列アクセス制御 (RCAC) | サポートされない |
|  | データのロードで使用する IBM InfoSphere Data Replication | サポートされない |
|  |  |
| ネットワーキング環境 | IBM Cloud Integrated Analytics | サポートされない |
|  | IBM Cloud Dedicated | サポートされない |
|  |  |
| セキュリティー・コンプライアンス | Health Information Portability and Accountability Act of 1996 (HIPAA) | サポートされない。サービス記述書を参照してください。|
|  | EU 一般データ保護規則 (GDPR) | サポートされない。サービス記述書を参照してください。|
|  |  |
| アカウント管理 | 再アクティブ化 | 30 日ごとに再アクティブ化が必要。再アクティブ化されない場合、無料プラン・サービスは 60 日後に削除されます。|
{: caption="表 1. {{site.data.keyword.Db2_on_Cloud_short}} 無料プランの制約事項" caption-side="top"}


