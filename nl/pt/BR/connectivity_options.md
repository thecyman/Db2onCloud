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

# Opções de conectividade
{: #connect_options}

O {{site.data.keyword.Db2_on_Cloud_long}} oferece várias opções de conectividade segura, dependendo dos requisitos de conexão dos aplicativos.  
{: shortdesc}

## Conectando-se a um terminal público (opção padrão)
{: #pub_endpt}

Como com qualquer serviço de nuvem pública, é possível conectar seu aplicativo por meio de
um nome de host público que é fornecido para você no momento em que seu serviço é provisionado. O
acesso aos seus dados é protegido por uma autenticação forte, amplas opções de autorização do Db2
e controles de acesso, criptografia sobre a ligação e em repouso e as práticas de segurança e
conformidade da IBM para desenvolvimento e operações. Uma lista de desbloqueio de IPs opcional é oferecida. Crie um caso de Suporte IBM se você desejar ativar a lista de desbloqueio de IPs.

### Como conectar-se a um terminal público:
{: #pub_endpt_steps}

A maneira mais fácil de se conectar a seus dados é por meio do nome do host público que foi fornecido em sua carta de boas-vindas. Também é possível obter o nome do host e as credenciais conforme a seguir:

1. Efetue login no {{site.data.keyword.Db2_on_Cloud_short}} e clique em sua instância
de serviço.
2. Clique em **Credenciais de serviço**.
3. Clique em **Nova credencial** e, em seguida, clique em **Incluir**.
4. Após a criação das credenciais, na coluna `Actions`, clique em **Visualizar credenciais**.
5. No exemplo de documento JSON a seguir, observe os conteúdos dos campos nome do host, senha e nome do usuário. Você usa esses três componentes para fazer a conexão de terminal público:

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

   ![Acesso de rede pública ao {{site.data.keyword.cloud_notm}}](images/public_connection.png "Visualização gráfica da conexão do usuário com a nuvem")

## Conectando-se a um terminal privado: IBM Cloud Service Endpoint
{: #priv_endpt}

Se você tiver um aplicativo implementado em sua conta do {{site.data.keyword.cloud_notm}} e desejar conectá-lo ao seu banco de dados sem o tráfego de banco de dados fluir sobre quaisquer redes públicas, será possível usar a opção **{{site.data.keyword.cloud_notm}} Service Endpoint** ao solicitar seu banco de dados. Será fornecido a você um nome de host privado no momento em que o serviço for provisionado e será possível conectar-se a ele somente
de dentro de sua conta do {{site.data.keyword.cloud_notm}}.  

Para saber mais sobre a opção {{site.data.keyword.cloud_notm}} Service Endpoint,
veja [Service Endpoint: Sobre](/docs/services/service-endpoint?topic=service-endpoint-about#about).


### Como se conectar a um terminal privado com o IBM Cloud Service Endpoint
{: #priv_endpt_steps}

A comunicação privada de rede e terminal acontece por meio do serviço {{site.data.keyword.cloud_notm}} Service Endpoint. O serviço Service Endpoint facilita a
o roteamento rápido e seguro do tráfego de rede entre diferentes serviços do {{site.data.keyword.cloud_notm}}
e seu banco de dados por meio do painel traseiro de rede privada do {{site.data.keyword.cloud_notm}}. Esse roteamento de rede assegura que seus dados nunca sejam enviados para a Internet pública. 

Para uma introdução ao Service Endpoint, sua conta do {{site.data.keyword.cloud_notm}} deve estar ativada para roteamento e encaminhamento virtual (VRF). Para ativar sua conta, veja [Ativando sua conta para usar o Service Endpoint usando a CLI do IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

Após a sua conta ser ativada para VRF e o Service Endpoint ser ativado, siga as instruções que foram fornecidas em sua carta de boas-vindas.

Agora, é o momento de conectar-se à sua instância do {{site.data.keyword.Db2_on_Cloud_short}} de dentro de sua conta do {{site.data.keyword.cloud_notm}} por meio do endereço de rede
privada que foi fornecido em sua carta de boas-vindas.

## Conectando-se a um terminal privado: rede privada virtual (VPN)
{: #vpn}

Se você tiver um aplicativo implementado em uma rede privada que esteja fora do {{site.data.keyword.cloud_notm}} sem acesso à Internet pública e desejar conectá-lo ao seu
banco de dados por meio de uma conexão de rede privada virtual (VPN), será possível fazer a solicitação
no momento da solicitação do serviço ou abrindo um caso de Suporte IBM. Os engenheiros de rede IBM
ajudarão os seus engenheiros de rede a configurar o túnel VPN entre a sua rede privada e o {{site.data.keyword.cloud_notm}}.

### Como conectar-se a um terminal privado com uma VPN
{: #priv_endpt_vpn_steps}

Para estabelecer uma conexão VPN com seu banco de dados em nuvem atrás de um terminal público, [crie um caso de suporte do {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/unifiedsupport/cases/add){:external} que inclua os detalhes a seguir:

* **Tipo de suporte**: técnico 
* **Categoria**: bancos de dados 
* **Oferta**: selecione sua instância do {{site.data.keyword.Db2_on_Cloud_short}} 
* **Assunto**: solicitação de conexão VPN 
* **Descrição**: forneça as informações necessárias a seguir
  * **Endereço de peer da VPN do lado do cliente** (seu terminal VPN): `<IP Address>`
  * **Domínio de criptografia do lado do cliente** (seja específico no que é requerido - 10.0.0.0/8 não é funcional porque o endereçamento 10 também é usado no {{site.data.keyword.cloud_notm}} para serviços de back-end): `<Domain>`
  * **Hardware e versão de VPN do lado do cliente**: `<Hardware and Version number>`
  * **Contato de VPN do lado do cliente** (nome do contato técnico
e endereço de e-mail): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Opcional** (mude somente se os valores padrão a seguir não forem adequados):

  *Parâmetros IKE/ISAKMP (Fase I)*

  * **Método de criptografia**: IKEv1
  * **Criptografia IKE / Algoritmo de criptografia**: AES-256
  * **Algoritmo de autenticação**: SHA1
  * **Grupo DH**: grupo 5
  * **Tempo de vida da associação de segurança (segundos)**: 1d (86.400 segundos)

  *Parâmetros IPSEC (Fase II)*

  * **Criptografia IPsec / Algoritmo de criptografia**: AES-256
  * **Algoritmo de autenticação**: SHA1
  * **Grupo DH** (se usando PF-Secrecy): grupo 5
  * **Tempo de vida da associação de segurança (segundos)**: 3.600 segundos

Após o recebimento de sua solicitação, os técnicos do {{site.data.keyword.cloud_notm}} abrirão as portas de firewall apropriadas e incluirá o endereço IP na lista de desbloqueio. A comunicação e a resolução para a solicitação serão feitas por meio do chamado do chamado de Suporte do {{site.data.keyword.cloud_notm}}.

![Acesso de rede pública ao {{site.data.keyword.cloud_notm}} por meio de uma VPN](images/public_connection_vpn.png "Visualização gráfica da conexão do usuário com a nuvem")
