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

# 连接选项
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} 根据您的应用程序连接需求，为您提供了多个安全连接选项。  
{: shortdesc}

## 连接到公共端点（缺省选项）
{: #pub_endpt}

对于任何公共云服务，您可以使用供应服务时提供给您的公共主机名来连接应用程序。通过强认证、大量 Db2 授权选项和访问控制、线上和静态加密以及开发和操作的 IBM 安全和合规性做法，可以保护对您数据的访问。为您提供了可选的 IP 白名单。如果要启用 IP 白名单，请创建 IBM 支持案例。

### 如何连接到公共端点：
{: #pub_endpt_steps}

连接到您的数据的最简单方式是使用欢迎信中提供的公共主机名。您还可以通过以下方式来获取主机名和凭证：

1. 登录到 {{site.data.keyword.Db2_on_Cloud_short}} 并单击您的服务实例。
2. 单击**服务凭证**。
3. 单击**新建凭证**，然后单击**添加**。
4. 凭证创建后，在`操作`列下，单击**查看凭证**。
5. 在下面的 JSON 文档示例中，记下主机名、密码以及用户名字段中的内容。使用这三个组件来连接到公共端点：

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

   ![对 {{site.data.keyword.cloud_notm}} 的公用网络访问权](images/public_connection.png "用户到云连接的图形视图")

## 连接到专用端点：IBM Cloud Service Endpoint
{: #priv_endpt}

如果您有应用程序部署在 {{site.data.keyword.cloud_notm}} 帐户，并且不想通过任何公用网络的数据库流量将其连接到您的数据库，那么您可以在订购数据库时使用 **{{site.data.keyword.cloud_notm}} Service Endpoint** 选项。在供应服务时我们将向您提供专用的主机名，但您仅可以从 {{site.data.keyword.cloud_notm}} 帐户中对此专用主机进行连接。  

要了解有关 {{site.data.keyword.cloud_notm}} Service Endpoint 选项的更多信息，请参阅 [Service Endpoint：关于](/docs/services/service-endpoint?topic=service-endpoint-about#about)。


### 如何使用 IBM Cloud Service Endpoint 连接专用端点
{: #priv_endpt_steps}

专用网络和端点的通信可以通过 {{site.data.keyword.cloud_notm}} Service Endpoint 服务来进行。Service Endpoint 服务通过 {{site.data.keyword.cloud_notm}} 专用网络底板，可以让您轻松、快速且安全地在不同的 {{site.data.keyword.cloud_notm}} 服务和数据库之间路由网络流量。此网络路由可以确保您的数据永远不会流向公共互联网。 

要使用 Service Endpoint，必须启用您的 {{site.data.keyword.cloud_notm}} 帐户用于虚拟路由和转发 (VRF)。要启用帐户，请参阅[使用 IBM Cloud CLI 来启用帐户以使用 Service Endpoint](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)。

您的帐户启用了 VRF，并且 Service Endpoint 也启用了之后，请遵循欢迎信中提供的指示信息进行操作。

现在，您可以使用欢迎信中提供的专用网络地址从 {{site.data.keyword.cloud_notm}} 帐户连接到您的 {{site.data.keyword.Db2_on_Cloud_short}} 实例。

## 连接到专用端点：虚拟专用网络 (VPN)
{: #vpn}

如果您有应用程序部署在 {{site.data.keyword.cloud_notm}} 之外的专用网络上，但该网络对公共互联网又没有访问权限，所以您想要通过虚拟专用网络 (VPN) 连接将其连接到数据库，那么您可以在订购服务时或者通过开具 IBM 支持案例来发出请求。IBM 网络工程师将会协助您的网络工程师在您的专用网络和 {{site.data.keyword.cloud_notm}} 之间设置 VPN 通道。

### 如何使用 VPN 连接到专用端点
{: #priv_endpt_vpn_steps}

要建立与支持公共端点的云数据库的 VPN 连接，请[创建 {{site.data.keyword.cloud_notm}} 支持案例](https://cloud.ibm.com/unifiedsupport/cases/add){:external}，其中包括以下详细信息：

* **支持类型**：技术 
* **类别**：数据库 
* **产品**：选择 {{site.data.keyword.Db2_on_Cloud_short}} 实例 
* **主题**：VPN 连接请求 
* **描述**：提供以下所需信息
  * **客户端 VPN 对等地址**（您的 VPN 端点）：`<IP Address>`
  * **客户端加密域**（根据需要具体指定 – 10.0.0.0/8 是不可行的，因为 10 寻址也用于 {{site.data.keyword.cloud_notm}} 中用于后端服务）：`<Domain>`
  * **客户端 VPN 硬件和版本**：`<Hardware and Version number>`
  * **客户端 VPN 联系人**（技术联系人姓名和电子邮件地址）： 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **可选**（仅在以下缺省值不适用时才变更）：

  *IKE/ISAKMP 参数（阶段 I）*

  * **加密方法**：IKEv1
  * **IKE 加密/加密算法**：AES-256
  * **认证算法**：SHA1
  * **DH-Group**：第 5 组
  * **安全性关联生命周期（秒）**：1 天（86400 秒）

  *IPSEC 参数（阶段 II）*

  * **IPsec 加密/加密算法**：AES-256
  * **认证算法**：SHA1
  * **DH-Group**（如果使用 PF-Secrecy）：第 5 组
  * **安全性关联生命周期（秒）**：3600 秒

收到请求后，{{site.data.keyword.cloud_notm}} 技术人员会打开相应的防火墙端口，并将所提供的 IP 地址列入白名单。有关请求的通信和解决方案将通过 {{site.data.keyword.cloud_notm}} 支持案例凭单进行。

![通过 VPN 对 {{site.data.keyword.cloud_notm}} 的公用网络访问权](images/public_connection_vpn.png "用户到云连接的图形视图")
