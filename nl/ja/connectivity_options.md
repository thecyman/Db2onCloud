---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-08"

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

# 接続オプション
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} はアプリケーションの接続要件に応じて、複数のセキュアな接続オプションを提供します。  
{: shortdesc}

## パブリック・エンドポイントへの接続 (デフォルト・オプション)
{: #pub_endpt}

他のパブリック・クラウド・サービスと同様に、サービスのプロビジョニング時に提供されるパブリック・ホスト名を使用してアプリケーションを接続できます。データへのアクセスは、強力な認証、広範な Db2 認証オプションとアクセス制御、通信中の暗号化、および開発と運用のための IBM のセキュリティーおよびコンプライアンスの取り組みによって保護されています。オプションで IP ホワイトリスティングを使用できます。IP ホワイトリスティングを有効にする場合は、IBM サポート Case を作成してください。

### パブリック・エンドポイントに接続する方法:
{: #pub_endpt_steps}

データに接続する最も簡単な方法は、ウェルカム・レターに記載されているパブリック・ホスト名を使用することです。ホスト名と資格情報は次の方法でも取得できます。

1. {{site.data.keyword.Db2_on_Cloud_short}} にログインし、サービス・インスタンスをクリックします。
2. **「サービス資格情報」**をクリックします。
3. **「新規資格情報」**をクリックし、**「追加 (Add)」**をクリックします。
4. 資格情報が作成されたら、`「アクション」`列で**「資格情報の表示」**をクリックします。
5. 以下の JSON 資料の例では、ホスト名、パスワード、およびユーザー名の各フィールドの内容に注目してください。パブリック・エンドポイント接続を確立する際に、これら 3 つのコンポーネントを使用します。

   ```
   {
     "hostname": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "password": "DTPY7KXxhp_pKtjLSt",
     "https_url": "https://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "port": 50000,
     "ssldsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxx.services.dal.bluemix.net;PORT=50001;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPY7KXWxhp_pKtjLSt;Security=SSL;",
     "host": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "jdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "uri": "db2://bluadmin:DTPY7KXx1p_pKtjLSt@dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "db": "BLUDB",
     "dsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxxx.services.dal.bluemix.net;PORT=50000;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPYZunlWxhp_pKtjLSt;",
     "username": "bluadmin",
     "ssljdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50001/BLUDB:sslConnection=true;"
   }

   ```

   ![{{site.data.keyword.cloud_notm}}](images/public_connection.png)

## プライベート・エンドポイントへの接続: IBM Cloud サービス・エンドポイント
{: #priv_endpt}

アプリケーションが {{site.data.keyword.cloud_notm}} アカウントでデプロイされており、データベース・トラフィックがいずれのパブリック・ネットワークも経由することなくデータベースに接続するようにしたい場合、データベースを注文する際に **{{site.data.keyword.cloud_notm}} サービス・エンドポイント**・オプションを使用することができます。サービスのプロビジョニング時にプライベート・ホスト名が提供され、自分の {{site.data.keyword.cloud_notm}} アカウント内からのみ接続できます。  

{{site.data.keyword.cloud_notm}} サービス・エンドポイント・オプションについて詳しくは、[サービス・エンドポイント: 概要](/docs/services/service-endpoint?topic=service-endpoint-about#about)を参照してください。


### IBM Cloud サービス・エンドポイントを使用してプライベート・エンドポイントに接続する方法
{: #priv_endpt_steps}

プライベート・ネットワークおよびエンドポイント通信は、{{site.data.keyword.cloud_notm}} サービス・エンドポイント・サービスを経由して実行されます。このサービス・エンドポイント・サービスを使用すると、{{site.data.keyword.cloud_notm}} プライベート・ネットワーク・バックプレーンを介して、さまざまな {{site.data.keyword.cloud_notm}} サービスとデータベースの間のネットワーク・トラフィックを迅速かつ安全にルーティングできます。このネットワーク・ルーティングにより、データがパブリック・インターネットに流出しないことが保証されます。 

サービス・エンドポイントの使用を開始するには、{{site.data.keyword.cloud_notm}} アカウントで仮想ルーティングおよび転送 (VRF) を有効にする必要があります。アカウントを有効にするには、[IBM Cloud CLI を使用してサービス・エンドポイントを使用するためにアカウントを有効にする](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)を参照してください。

アカウントで VRF が有効になり、サービス・エンドポイントが有効になったら、ウェルカム・レターに記載されている手順に従ってください。

これで、ウェルカム・レターで指定されているプライベート・ネットワーク・アドレスを経由して、{{site.data.keyword.cloud_notm}} アカウント内から {{site.data.keyword.Db2_on_Cloud_short}} インスタンスに接続できるようになります。

## プライベート・エンドポイントへの接続: 仮想プライベート・ネットワーク (VPN)
{: #vpn}

パブリック・インターネットにアクセスせずに {{site.data.keyword.cloud_notm}} の外部にあるプライベート・ネットワーク上にデプロイされたアプリケーションがあり、仮想プライベート・ネットワーク (VPN) を介してそれをデータベースに接続したい場合、サービスを注文する時点で、または IBM サポート Case を開くことによって、その要求を行うことができます。ユーザーのネットワーク・エンジニアがプライベート・ネットワークと {{site.data.keyword.cloud_notm}} の間に VPN トンネルを設定する際には、IBM ネットワーク・エンジニアがサポートします。

### VPN を使用してプライベート・エンドポイントに接続する方法
{: #priv_endpt_vpn_steps}

パブリック・エンドポイントの背後でクラウド・データベースへの VPN 接続を確立するには、以下の詳細を含む [{{site.data.keyword.cloud_notm}} サポート Case を作成します![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://cloud.ibm.com/unifiedsupport/cases/add){:new_window}。

* **サポートのタイプ**: テクニカル 
* **カテゴリー**: データベース 
* **オファリング**: ご使用の {{site.data.keyword.Db2_on_Cloud_short}} インスタンスを選択します 
* **サブジェクト**: VPN 接続要求 
* **説明**: 以下の必要情報を入力します
  * **お客様の VPN ピア・アドレス** (ご使用の VPN エンドポイント): `<IP Address>`
  * **お客様の暗号化ドメイン** (必要な情報を具体的に記載してください – 10 アドレッシングは {{site.data.keyword.cloud_notm}} 内でバックエンド・サービス用に使用済みであるため、10.0.0.0/8 は動作しません): `<Domain>`
  * **お客様の VPN ハードウェア & バージョン**: `<Hardware and Version number>`
  * **お客様の VPN 連絡先** (技術担当者の名前と E メール・アドレス): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **オプション** (以下のデフォルト値が適切でない場合にのみ変更してください):

  *IKE/ISAKMP パラメーター (フェーズ I)*

  * **暗号化方式**: IKEv1
  * **IKE 暗号化 / 暗号化アルゴリズム**: AES-256
  * **認証アルゴリズム**: SHA1
  * **DH グループ**: グループ 5
  * **セキュリティー・アソシエーションの存続時間 (秒)**: 1 日 (86400 秒)

  *IPSEC パラメーター (フェーズ II)*

  * **IPsec 暗号化 / 暗号化アルゴリズム**: AES-256
  * **認証アルゴリズム**: SHA1
  * **DH グループ** (PF-Secrecy を使用している場合): グループ 5
  * **セキュリティー・アソシエーションの存続時間 (秒)**: 3600 秒

要求を受け取った後、{{site.data.keyword.cloud_notm}} 技術者は適切なファイアウォール・ポートを開き、提供された IP アドレスをホワイトリストに追加します。要求に対するコミュニケーションや解決策は、{{site.data.keyword.cloud_notm}} サポート Case  チケットを通じて行われます。

![{{site.data.keyword.cloud_notm}}](images/public_connection_vpn.png)
