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

# Opzioni di connettività
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} offre molteplici opzioni di connettività protette, a seconda dei tuoi requisiti di connessione dell'applicazione.  
{: shortdesc}

## Connessione a un endpoint pubblico (opzione predefinita)
{: #pub_endpt}

Con qualsiasi servizio cloud pubblico, puoi connettere la tua applicazione mediante un nome host pubblico che ti è stato fornito quando è stato eseguito il provisioning del tuo servizio. L'accesso ai tuoi dati è protetto da un'autenticazione avanzata, ampi controlli di accesso e opzioni di autorizzazione DB2, crittografia dei dati in transito e inattivi e prassi di conformità e sicurezza IBM per lo sviluppo e le operazioni. Viene offerto, facoltativamente, un inserimento in whitelist dell'IP. Crea un caso di supporto IBM se desideri abilitare l'inserimento in whitelist dell'IP.

### Come connettersi a un endpoint pubblico:
{: #pub_endpt_steps}

Il modo più facile per connetterti ai tuoi dati è mediante il nome host pubblico che era stato fornito nella tua lettera di benvenuto. Puoi anche ottenere il tuo nome host e le tue credenziali nel seguente modo:

1. Esegui l'accesso a {{site.data.keyword.Db2_on_Cloud_short}} e fai clic sulla tua istanza del servizio.
2. Fai clic su **Credenziali del servizio**.
3. Fai clic su **Nuova credenziale** e fai quindi clic su **Aggiungi**.
4. Dopo che le credenziali sono state create, nella colonna `Azioni` fai clic su **Visualizza credenziali**.
5. Nel seguente esempio di documento JSON, nota il contenuto dei campi hostname, password e username. Utilizzi questi tre componenti per stabilire la connessione all'endpoint pubblico:

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

   ![Accesso di rete pubblica a {{site.data.keyword.cloud_notm}}](images/public_connection.png "Vista geografica della connessione da utente al cloud")

## Connessione a un endpoint privato: IBM Cloud Service Endpoint
{: #priv_endpt}

Se hai un'applicazione distribuita sul tuo account {{site.data.keyword.cloud_notm}} e desideri connetterla al tuo database senza che il traffico di database fluisca su qualsiasi rete pubblica, puoi utilizzare l'opzione **{{site.data.keyword.cloud_notm}} Service Endpoint** quando ordini il tuo database. Ti viene fornito un nome host privato quando viene eseguito il provisioning del servizio e puoi solo connetterti a esso dall'interno del tuo account {{site.data.keyword.cloud_notm}}.  

Per ulteriori informazioni sull'opzione {{site.data.keyword.cloud_notm}} Service Endpoint, vedi [Service Endpoint: About](/docs/services/service-endpoint?topic=service-endpoint-about#about).


### Come stabilire una connessione a un endpoint privato con IBM Cloud Service Endpoint
{: #priv_endpt_steps}

Le comunicazioni di rete privata ed endpoint avvengono mediante il servizio {{site.data.keyword.cloud_notm}} Service Endpoint. Il servizio Service Endpoint rende facile instradare rapidamente e in modo protetto il traffico di rete tra diversi servizi {{site.data.keyword.cloud_notm}} e il tuo database sul backplane di rete privata {{site.data.keyword.cloud_notm}}. Questo instradamento di rete garantisce che i tuoi dati non vadano mai sull'internet pubblico. 

Per iniziare a lavorare con Service Endpoint, il tuo account {{site.data.keyword.cloud_notm}} deve essere abilitato per VRF (virtual routing and forwarding). Per fare in modo che il tuo account venga abilitato, vedi [Enabling your account for using Service Endpoint by using IBM Cloud CLI](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

Dopo che il tuo account è stato abilitato a VRF e Service Endpoint è stato abilitato, attieniti alle istruzioni che erano state fornite nella tua lettera di benvenuto.

Ora è il momento di stabilire una connessione alla tua istanza {{site.data.keyword.Db2_on_Cloud_short}} dall'interno del tuo account {{site.data.keyword.cloud_notm}} mediante l'indirizzo di rete privato che era stato fornito nella tua lettera di benvenuto.

## Connessione a un endpoint privato: VPN (virtual private network)
{: #vpn}

Se hai un'applicazione distribuita su una rete privata che si trova fuori da {{site.data.keyword.cloud_notm}} senza accesso all'internet pubblico e desideri connetterla al tuo database su una connessione VPN (virtual private network), puoi fare la richiesta quando ordini il servizio oppure aprendo un caso di supporto IBM. Gli ingegneri di rete IBM assisteranno i tuoi ingegneri di rete per configurare il tunnel VPN tra la tua rete privata e {{site.data.keyword.cloud_notm}}.

### Come connettersi a un endpoint privato con una VPN
{: #priv_endpt_vpn_steps}

Per stabilire una connessione VPN al tuo database cloud dietro un endpoint pubblico, [crea un caso di supporto {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/unifiedsupport/cases/add){:external} che include i seguenti dettagli:

* **Type of support**: Technical 
* **Category**: Databases 
* **Offering**: seleziona la tua istanza {{site.data.keyword.Db2_on_Cloud_short}} 
* **Subject**: VPN Connection Request 
* **Description**: fornisci le seguenti informazioni obbligatorie
  * **Customer-side VPN Peer Address** (il tuo endpoint VPN): `<IP Address>`
  * **Customer-side Encryption Domain** (sii specifico in merito a ciò che è richiesto – 10.0.0.0/8 non è proponibile perché l'indirizzamento 10 è utilizzato anche in {{site.data.keyword.cloud_notm}} per i servizi di backend): `<Domain>`
  * **Customer-side VPN Hardware & Version**: `<Hardware and Version number>`
  * **Customer-side VPN Contact** (nome e indirizzo email del contatto tecnico): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Facoltativo** (apporta modifiche solo se i seguenti valori predefiniti non sono adatti):

  *Parametri IKE/ISAKMP (fase I)*

  * **Encryption Method**: IKEv1
  * **IKE Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group**: Group 5
  * **Security Association Lifetime (seconds)**: 1d (86400 secondi)

  *Parametri IPSEC (fase II)*

  * **IPsec Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group** (if using PF-Secrecy): Group 5
  * **Security Association Lifetime (seconds)**: 3600 secondi

Dopo la ricezione della tua richiesta, i tecnici {{site.data.keyword.cloud_notm}} apriranno le porte del firewall appropriate e inseriranno in whitelist l'indirizzo IP fornito. Le comunicazioni e la risoluzione alla richiesta verranno effettuate tramite il ticket del caso di supporto {{site.data.keyword.cloud_notm}}.

![Accesso di rete pubblica a {{site.data.keyword.cloud_notm}} tramite una VPN](images/public_connection_vpn.png "Vista geografica della connessione da utente al cloud")
