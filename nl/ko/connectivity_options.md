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

# 연결 옵션
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}}에서는 애플리케이션 연결 요구사항에 따라 여러 소스 연결 옵션을 제공합니다.  
{: shortdesc}

## 공용 엔드포인트에 연결(기본 옵션)
{: #pub_endpt}

모든 퍼블릭 클라우드 서비스와 마찬가지로, 서비스가 프로비저닝될 때 제공되는 공용 호스트 이름을 사용하여 애플리케이션을 연결할 수 있습니다. 사용자의 데이터에 대한 액세스는 강력한 인증, 광범위한 Db2 권한 부여 옵션 및 액세스 제어, 전송 중 및 저장 시 암호화, 그리고 개발 및 운영에 대한 IBM 보안 및 규제 준수 관행으로 보호됩니다. 선택적 IP 화이트리스트 지정이 제공됩니다. IP 화이트리스트 지정을 사용하도록 설정하려면 IBM 지원 케이스를 작성하십시오. 

### 공용 엔드포인트에 연결하는 방법
{: #pub_endpt_steps}

사용자의 데이터에 연결하는 가장 쉬운 방법은 환영 이메일에 제공된 공용 호스트 이름을 사용하는 것입니다. 다음과 같은 방법으로 호스트 이름과 인증 정보를 얻을 수도 있습니다.

1. {{site.data.keyword.Db2_on_Cloud_short}}에 로그인하여 서비스 인스턴스를 클릭하십시오.
2. **서비스 인증 정보**를 클릭하십시오.
3. **새 인증 정보**를 클릭한 다음 **추가**를 클릭하십시오.
4. 인증 정보가 작성된 후 `조치` 열에서 **인증 정보 보기**를 클릭하십시오.
5. 다음 JSON 문서 예에서 hostname, password 및 username 필드의 내용을 기록해 두십시오. 이 세 컴포넌트를 사용하여 공용 엔드포인트 연결을 수행합니다.

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

   ![{{site.data.keyword.cloud_notm}}}에 대한 공용 네트워크 액세스](images/public_connection.png "사용자와 클라우드 간 연결의 그래픽 보기")

## 사설 엔드포인트에 연결: IBM Cloud Service Endpoint
{: #priv_endpt}

{{site.data.keyword.cloud_notm}} 계정에 배치된 애플리케이션이 있으며 데이터베이스 트래픽이 공용 네트워크를 통해 플로우되지 않도록 하면서 이 애플리케이션을 데이터베이스에 연결하려는 경우에는 데이터베이스를 주문할 때 **{{site.data.keyword.cloud_notm}} Service Endpoint** 옵션을 사용할 수 있습니다. 서비스가 프로비저닝될 때 사설 호스트 이름이 제공되며 사용자의 {{site.data.keyword.cloud_notm}} 계정 내에서만 여기에 연결할 수 있습니다.  

{{site.data.keyword.cloud_notm}} Service Endpoint 옵션에 대해 자세히 알아보려면 [Service Endpoint: 정보](/docs/services/service-endpoint?topic=service-endpoint-about#about)를 참조하십시오.


### IBM Cloud Service Endpoint를 통해 사설 엔드포인트에 연결하는 방법
{: #priv_endpt_steps}

사설 네트워크 및 엔드포인트 통신은 {{site.data.keyword.cloud_notm}} Service Endpoint 서비스를 통해 이루어집니다. Service Endpoint 서비스는 {{site.data.keyword.cloud_notm}} 사설 네트워크 백플레인을 통해 다양한 {{site.data.keyword.cloud_notm}} 서비스와 데이터베이스 간에 네트워크 트래픽을 쉬우면서도 빠르고 안전하게 라우팅할 수 있게 해 줍니다. 이 네트워크 라우팅은 데이터가 공용 인터넷으로 나가지 않도록 보장합니다. 

Service Endpoint를 시작하려면 {{site.data.keyword.cloud_notm}} 계정에서 VRF(Virtual Routing and Forwarding)이 사용으로 설정되어야 합니다. 계정에서 이를 사용으로 설정하려면 [IBM Cloud CLI를 사용하여 Service Endpoint를 사용하도록 계정 설정](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps)을 참조하십시오.

계정에서 VRF가 사용으로 설정되고 Service Endpoint가 사용으로 설정된 후에는 환영 이메일에 제공된 지시사항을 따르십시오.

이제 환영 이메일에 제공된 사설 네트워크 주소를 통해 사용자의 {{site.data.keyword.cloud_notm}} 계정에서 {{site.data.keyword.Db2_on_Cloud_short}} 인스턴스에 연결할 차례입니다.

## 사설 엔드포인트에 연결: 가상 사설망(VPN)
{: #vpn}

공용 인터넷에 대한 액세스가 없는 {{site.data.keyword.cloud_notm}} 외부의 사설 네트워크에 배치된 애플리케이션이 있으며 이를 가상 사설망(VPN) 연결을 통해 데이터베이스에 연결하려는 경우에는 서비스를 주문할 때 또는 IBM 지원 케이스를 열어 요청할 수 있습니다. 사용자의 사설 네트워크와 {{site.data.keyword.cloud_notm}} 간에 VPN 터널을 설정할 수 있도록 IBM 네트워크 엔지니어가 사용자 측의 네트워크 엔지니어를 지원합니다.

### VPN을 통해 사설 엔드포인트에 연결하는 방법
{: #priv_endpt_vpn_steps}

공용 엔드포인트 뒤에 있는 클라우드 데이터베이스에 VPN 연결을 설정하려면 다음 세부사항을 포함하는 [{{site.data.keyword.cloud_notm}} 지원 케이스를 작성](https://cloud.ibm.com/unifiedsupport/cases/add){:external}하십시오.

* **지원 유형**: 기술 
* **카테고리**: 데이터베이스 
* **오퍼링**: 사용자의 {{site.data.keyword.Db2_on_Cloud_short}} 인스턴스 선택 
* **제목**: VPN 연결 요청 
* **설명**: 다음의 필수 정보 제공
  * **고객 측 VPN 피어 주소**(사용자의 VPN 엔드포인트): `<IP Address>`
  * **고객 측 암호화 도메인**(필요한 항목을 구체적으로 지정해야 함 – 10 주소 지정은 {{site.data.keyword.cloud_notm}} 내에서 백엔드 서비스용으로도 사용되므로 10.0.0.0/8은 불가능함): `<Domain>`
  * **고객 측 VPN 하드웨어 & 버전**: `<Hardware and Version number>`
  * **고객 측 VPN 담당자**(기술 담당자 이름 및 이메일 주소): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **선택사항**(다음 기본값이 적합하지 않을 경우에만 변경하십시오.):

  *IKE/ISAKMP 매개변수(단계 I)*

  * **암호화 방법**: IKEv1
  * **IKE 암호화 / 암호화 알고리즘**: AES-256
  * **인증 알고리즘**: SHA1
  * **DH 그룹**: 그룹 5
  * **보안 연관 수명(초)**: 1일(86400초)

  *IPSEC 매개변수(단계 II)*

  * **IPsec 암호화 / 암호화 알고리즘**: AES-256
  * **인증 알고리즘**: SHA1
  * **DH 그룹**(PF-Secrecy를 사용하는 경우): 그룹 5
  * **보안 연관 수명(초)**: 3600초

요청이 수신되면 {{site.data.keyword.cloud_notm}} 기술자가 적절한 방화벽 포트를 열고 제공된 IP 주소를 화이트리스트로 지정합니다. 요청에 대한 커뮤니케이션 및 해결은 {{site.data.keyword.cloud_notm}} 지원 케이스 티켓을 통해 이루어집니다.

![VPN을 통한 {{site.data.keyword.cloud_notm}}에 대한 공용 네트워크 액세스](images/public_connection_vpn.png "사용자와 클라우드 간 연결의 그래픽 보기")
