---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-08"

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

# 連線功能選項
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} 提供多個安全的連線功能選項，取決於您的應用程式連線需求。  
{: shortdesc}

## 連接至公用端點（預設選項）
{: #pub_endpt}

如同任何公用雲端服務，您可以藉由在佈建服務時提供給您的公用主機名稱，來連接您的應用程式。存取資料時會受到下列方式保護：強型態鑑別、大量 Db2 授權選項及存取控制、線上及靜態加密，以及用於開發及作業的 IBM 安全及法規遵循作法。系統會提供選用性的 IP 白名單。如果您想要啟用 IP 白名單，請建立 IBM 支援案例。

### 如何連接至公用端點：
{: #pub_endpt_steps}

連接至資料時最輕鬆的方式，是藉由您歡迎使用信函中提供的公用主機名稱。您可以採用下列方式取得主機名稱及認證：

1. 登入 {{site.data.keyword.Db2_on_Cloud_short}} 並按一下您的服務實例。
2. 按一下**服務認證**。
3. 按一下**新建認證**，然後按一下**新增**。
4. 在建立認證之後，請在`動作`欄之下，按一下**檢視認證**。
5. 在下列 JSON 文件範例中，記下主機名稱、密碼及使用者名稱欄位的內容。您可以使用這三個元件來進行公用端點連線：

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

   ![對 {{site.data.keyword.cloud_notm}} 的公用網路存取權](images/public_connection.png "使用者對雲端連線的圖形視圖"){: caption="圖 1. 對 {{site.data.keyword.cloud_notm}} 的公用網路存取權" caption-side="bottom"}

## 連接至專用端點：IBM Cloud Service Endpoint
{: #priv_endpt}

如果您已將應用程式部署在 {{site.data.keyword.cloud_notm}} 帳戶上，而且想要將它連接至資料庫，而不讓資料庫資料流量流過任何公用網路，則可以在訂購資料庫時使用 **{{site.data.keyword.cloud_notm}} Service Endpoint** 選項。佈建服務時將提供您一個專用主機名稱，而且您只能從 {{site.data.keyword.cloud_notm}} 帳戶內連接至其中。  

若要進一步瞭解 {{site.data.keyword.cloud_notm}} Service Endpoint 選項，請參閱 [Service Endpoint：關於](/docs/services/service-endpoint?topic=service-endpoint-about#about)。


### 如何使用 IBM Cloud Service Endpoint 連接至專用端點
{: #priv_endpt_steps}

專用網路與端點通訊係藉由 {{site.data.keyword.cloud_notm}} Service Endpoint 服務發生。Service Endpoint 服務可讓您輕鬆地透過 {{site.data.keyword.cloud_notm}} 專用網路背板，在不同的 {{site.data.keyword.cloud_notm}} 服務與您的資料庫之間快速且安全地遞送網路資料流量。此網路遞送確保您的資料絕對不會外送至公用網際網路。 

若要開始使用 Service Endpoint，必須啟用您的 {{site.data.keyword.cloud_notm}} 帳戶，進行虛擬遞送及轉遞 (VRF)。若要啟用您的帳戶，請參閱[使用 IBM Cloud CLI 讓您的帳戶可以使用 Service Endpoint](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)。

在您的帳戶啟用 VRF 且 Service Endpoint 啟用之後，請遵循歡迎使用信函中提供的指示。

現在，是時候從 {{site.data.keyword.cloud_notm}} 帳戶內藉由歡迎使用信函中提供的專用網路位址連接至 {{site.data.keyword.Db2_on_Cloud_short}} 實例。

## 連接至專用端點：虛擬專用網路 (VPN)
{: #vpn}

如果您已將應用程式部署在 {{site.data.keyword.cloud_notm}} 外的專用網路上，該網路無法存取公用網際網路，並且您想要透過虛擬專用網路 (VPN) 將其連接至資料庫，則可在訂購服務時提出要求，或是藉由開立 IBM 支援案例來提出要求。IBM 網路工程師會協助您的網路工程師在專用網路與 {{site.data.keyword.cloud_notm}} 之間設定 VPN 通道。

### 如何使用 VPN 連接至專用端點
{: #priv_endpt_vpn_steps}

若要在公用端點後面建立雲端資料庫的 VPN 連線，請[建立 {{site.data.keyword.cloud_notm}} 支援案例](https://cloud.ibm.com/unifiedsupport/cases/add){:external}，其中包括下列詳細資料：

* **支援類型**：技術 
* **種類**：資料庫 
* **供應項目**：選取您的 {{site.data.keyword.Db2_on_Cloud_short}} 實例 
* **主旨**：VPN 連線要求 
* **說明**：提供下列必要資訊
  * **客戶端 VPN 對等位址**（您的 VPN 端點）：`<IP Address>`
  * **客戶端加密網域**（請明確指明所需項目 – 10.0.0.0/8 無法運作，因為 10 定址也會在 {{site.data.keyword.cloud_notm}} 內用於後端服務）：`<Domain>`
  * **客戶端 VPN 硬體及版本**：`<Hardware and Version number>`
  * **客戶端 VPN 聯絡人**（技術聯絡人名稱及電子郵件位址）： 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **選用**（僅在下列預設值不適用時才會變更）：

  *IKE/ISAKMP 參數（階段 I）*

  * **加密方法**：IKEv1
  * **IKE 加密/加密演算法**：AES-256
  * **鑑別演算法**：SHA1
  * **DH-Group**：群組 5
  * **安全關聯生命期限（秒）**：1 日（86400 秒）

  *IPSEC 參數（階段 II）*

  * **IPsec 加密/加密演算法**：AES-256
  * **鑑別演算法**：SHA1
  * **DH-Group**（如果使用 PF-Secrecy）：群組 5
  * **安全關聯生命期限（秒）**：3600 秒

在收到您的要求之後，{{site.data.keyword.cloud_notm}} 技術人員將開啟適當的防火牆埠，並將提供的 IP 位址列入白名單中。要求的通訊及解析將透過 {{site.data.keyword.cloud_notm}} 支援案例問題單來進行。

![透過 VPN 對 {{site.data.keyword.cloud_notm}} 的公用網路存取權](images/public_connection_vpn.png "使用者對雲端連線的圖形視圖"){: caption="圖 2. 透過 VPN 對 {{site.data.keyword.cloud_notm}} 的公用網路存取權" caption-side="bottom"}
