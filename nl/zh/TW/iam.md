---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-21"

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

# IBM Cloud 上的 Identity and Access Management (IAM)
{: #iam}

Identity and Access Management (IAM) 可讓您安全地鑑別平台服務的使用者，並在 {{site.data.keyword.Bluemix_notm}} 平台間一致地控制對資源的存取。例如，只要以您的 IBM ID 單一登入 {{site.data.keyword.Bluemix_notm}}，您就能夠存取任何服務主控台及其應用程式，而無需個別登入每個服務主控台及其應用程式。
{: shortdesc}

## 是否在您的實例上啟用了 IAM？
{: #enabled}

在一段時間內，將啟用 {{site.data.keyword.Bluemix_notm}} 上 {{site.data.keyword.Db2_on_Cloud_long}} 管理的資料庫實例，以使用 IAM 進行存取控制。若要檢查是否已在您的實例上啟用 IAM，請執行下列查詢：

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

如果 **IAM_ENABLED** 的回覆值為 1，則表示已在您的實例上啟用 IAM。

## IBM Cloud IAM 的特性
{: #features}

已使用兩種支援身分針對 {{site.data.keyword.Db2_on_Cloud_short}} 管理的服務實作下列 IAM 特性：

**IBM ID**

資料庫管理者必須透過主控台或 REST API 將擁有 IBM ID 的使用者新增至每個資料庫服務實例，這些使用者才能連接至特定資料庫服務實例。就像非 IBM ID 使用者一樣，必須在新增 IBM ID 使用者的同時，輸入資料庫服務實例的使用者 ID。這個使用者 ID 在資料庫服務實例內必須是唯一的。這個使用者 ID 也是資料庫內的授權 (AUTH) ID。資料庫管理者可以根據 AUTH ID 授與及撤銷許可權。

**服務 ID**

服務 ID 識別服務或應用程式的方式，與使用者 ID 識別使用者的方式類似。服務 ID 是應用程式可用來向 IBM Cloud 服務進行鑑別的 ID。服務 ID 代表有別於擁有之 IBM ID 的實體。因此，可以授與資料庫內服務 ID 特有的不同權限及許可權。服務 ID 沒有密碼。您必須為每個服務 ID 建立 API 金鑰，才能讓服務 ID 連接至資料庫服務實例。如需服務 ID 的相關資訊，請參閱：[IBM Cloud IAM 服務 ID 及 API 金鑰簡介 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}。

## 用戶端連線及使用者登入
{: #connect_user}

**必備項目**：Db2 Client 11.1 版 FP3 以及更新版本。

下列方法可用於 IAM 鑑別：

**存取記號**

應用程式可以使用 API 金鑰透過 REST API 直接從 IAM 服務取得存取記號。如需相關資訊，請參閱：[使用 API 金鑰取得 IBM Cloud IAM 記號 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}。存取記號在其到期前的預設有效期間為 60 分鐘。如果記號已過期，則 Db2 伺服器不容許建立連線。在建立連線之後，不會檢查記號是否到期。就像在 IAM 整合之前一樣，連線將保持連接，直到應用程式中斷連接或連線因其他原因而終止。

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

存取記號可向資料庫識別 IBM ID 使用者或服務 ID。資料庫伺服器會先驗證存取記號的有效性，再接受存取記號。如果應用程式需要連接至多個資料庫服務實例或其他 {{site.data.keyword.Bluemix_notm}} 服務實例，這是最好的方法，因為它會將與 IAM 服務的通訊降到最少以驗證存取記號。

**API 金鑰**

您可以為每個 IBM ID 使用者或服務 ID 建立多個 API 金鑰。每個 API 金鑰通常是針對單一應用程式建立的。只要擁有的 IBM ID 或服務 ID 新增為資料庫服務實例的使用者，就容許應用程式連接至相同的資料庫服務實例。API 金鑰在資料庫內具有與所擁有 IBM ID 或服務 ID 相同的權限及許可權。如果不再容許應用程式連接至資料庫，則可以移除相對應的 API 金鑰。比起使用存取記號，這個鑑別方法在應用程式中所需的變更較少，因為它不需要與 IAM 服務直接互動。如需建立及管理 API 金鑰的相關資訊，請參閱：[管理使用者 API 金鑰 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}。

**IBM ID/密碼**

IBM ID/密碼可用來登入主控台，也可以利用容許使用者 ID/密碼的相同方法在應用程式內使用。聯合 IBM ID 時會發生異常狀況，因為無法完成重新導向至組織登入頁面的作業。不過，讓應用程式建立資料庫服務實例連線的建議方法是使用存取記號。

## 支援的介面
{: #sup-if}

支援下列資料庫用戶端介面：

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC、CLP 及 CLPPLUS
{: #odbc-clpplus}

如果是要使用 IAM 鑑別連接至 Db2 伺服器的 ODBC 應用程式或指令行用戶端（CLP、CLPPLUS），必須執行下列指令，先在 `db2dsdriver.cfg` 設定檔中設定資料來源名稱 (DSN)：

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

`db2dsdriver.cfg` 配置檔是一個 XML 檔案，通常位於 `sqllib/cfg` 目錄，其中包含 DSN 別名及其內容的清單。

下列 `db2dsdriver.cfg` 配置檔的範例顯示用來建立資料庫服務實例連線的配置。此配置檔提供 DSN 別名、資料庫名稱、主機名稱（或 IP 位址），以及**鑑別**類型和 **SecurityTransportMode** 參數值：

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<configuration>
        <dsncollection>
        <dsn alias="<data_source_name>" name="bludb" host="<host_name_or_IP_address>" port="50001">
            <parameter name="Authentication" value="GSSPLUGIN"/>
            <parameter name="SecurityTransportMode" value="SSL"/>
        </dsn>
        </dsncollection>
        <databases>
            <database name="bludb" host="<host_name_or_IP_address>" port="50001"/>
        </databases>
</configuration>
```

* ODBC 連線字串可以包含下列其中一項：

    **存取記號**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **API 金鑰**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBM ID/密碼**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    如果是 ODBC，您可以在 `db2dsdriver.cfg` 配置檔或應用程式的連線字串中指定 **AUTHENTICATION=GSSPLUGIN**。

* CLP CONNECT 陳述式可以包含下列其中一項：

    **存取記號**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，連接至資料庫伺服器 `<database_server_name>` 並傳遞存取記號：

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **API 金鑰**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，使用 API 金鑰連接至資料庫伺服器 `<database_server_name>`：

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBM ID/密碼**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，使用 IBM ID/密碼連接至資料庫伺服器 `<database_server_name>`：

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    如需使用 CLP 連接至資料庫伺服器的詳細資料，請參閱：[CONNECT（類型 2）陳述式 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}。 

* CLPPLUS CONNECT 陳述式可以包含下列其中一項：

    **存取記號**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，以連接至 DSN 別名 (`@<data_source_name>`) 並傳遞存取記號：

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **API 金鑰**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，以使用 API 金鑰連接至 DSN 別名 (`@<data_source_name>`)：

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBM ID/密碼**

    在 CLPPLUS 命令提示字元或 Script 中執行下列指令，以使用 IBM ID/密碼連接至 DSN 別名 (`@<data_source_name>`)：

    `connect <IBMid>/<password>@<data_source_name>`

    如需使用 CLPPLUS 連接至 DSN 別名的詳細資料，請參閱：[CLPPlus 中的 DSN 別名 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}。

### JDBC
{: #jdbc}

IAM 鑑別支援第 4 類 JDBC 驅動程式。

下列範例顯示三種方法的連線 Snippet：

**存取記號**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setAccessToken( "<access_token>" );
Connection conn = dataSource.getConnection( );
```

或

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**API 金鑰**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setApiKey( "<api_key>" );
Connection conn = dataSource.getConnection( );
```

或

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apikey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBM ID/密碼**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<IBMid>", "<password>" );
```

或

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## 主控台使用者體驗
{: #console-ux}

服務主控台登入頁面具有使用 IBM ID 和密碼登入的選項。按一下**透過 IBM ID 登入**按鈕之後，使用者會導向至在其中輸入密碼的 IAM 登入頁面。完成鑑別後，使用者會重新導向回主控台。資料庫管理者必須透過主控台或 REST API 將 IBM ID 使用者新增至每個資料庫服務實例，這類登入才能順利完成。就像非 IBM ID 使用者一樣，必須在新增 IBM ID 使用者的同時，輸入資料庫服務實例的使用者 ID。此使用者 ID 在資料庫服務實例內必須是唯一的。這個使用者 ID 也是資料庫內的授權 (AUTH) ID。

## REST API 體驗
{: #api}

{{site.data.keyword.Db2_on_Cloud_short}} REST API 已經過加強，可讓先前接受資料庫服務所產生存取記號的功能也接受 IAM 存取記號。

* 若要新增 IBM ID，請執行下列範例 API 呼叫：

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  `"id"` 及 `"ibmid"` 的 `<userid>` 值不必相同。這兩個不同的 ID 不會以任何方式鏈結在一起。{: note}

* 若要移轉現有的非 IBM ID 資料庫使用者（例如 `abcuser`）並使他們成為 IBM ID 使用者，首先請執行下列範例 API 呼叫來刪除非 IBM ID 使用者 ID：

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  接下來，執行下列範例 API 呼叫，重新新增 IBM ID 與先前的使用者 ID (`abcuser`) 相同的使用者：

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  因為使用者 ID (`abcuser`) 與該使用者的新 IBM ID 仍然相同，所以授與該使用者的資料庫許可權保持不變。如果需要移轉現有的非 IBM ID 資料庫使用者清單使他們成為 IBM ID 使用者，您必須為每位使用者執行上述的一對 API 呼叫。

* 若要一次新增多個 IBM ID 使用者，請建立列出下列範例 API 呼叫（每個使用者各一個）的批次檔：

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

如需服務 API 的詳細資料，請參閱：[{{site.data.keyword.Db2_on_Cloud_short}} REST API ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://ibm.biz/db2oc_api){:new_window}。

## IBM ID 聯合
{: #fed_ibmid}

若要使用您自己的身分提供者（例如 LDAP），您必須先使用 IBM ID 聯合 LDAP 伺服器。如需使用 IBM ID 聯合 LDAP 伺服器的指示，請參閱：[IBMid Enterprise Federation Adoption Guide ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}。在 IBM ID 聯合完成且資料庫管理者將容許的使用者新增至資料庫服務實例之後，這些使用者就可以使用他們的公司使用者 ID 和密碼登入主控台。或者，這些使用者可以使用代表其使用者 ID 的存取記號或 API 金鑰，透過其中一個支援的資料庫用戶端介面連接至資料庫服務實例。

## 限制
{: #restrictions}

以下是與 IAM 鑑別有關的限制：

* 只有透過 SSL 連線才支援連接至 Db2 伺服器的 Db2 用戶端 IAM 鑑別。
* 支援 IBM ID 聯合以容許將自訂使用者管理入口網站或伺服器用於鑑別。這類支援未包含任何群組聯合。
* 不支援資料庫聯合的 IAM 鑑別。
* 不支援透過 CLPPlus 執行 IDA 及使用者定義延伸 (UDX) 指令。
* 不支援第 2 類 JDBC 驅動程式。




