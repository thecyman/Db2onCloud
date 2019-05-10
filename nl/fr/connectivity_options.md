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

# Options de connectivité
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} offre plusieurs options de connexion sécurisée en fonction de vos besoins de connexion d'application.  
{: shortdesc}

## Connexion à un noeud final public (option par défaut)
{: #pub_endpt}

Comme avec tout service de cloud public, vous pouvez connecter votre application par le biais d'un nom d'hôte public fourni au moment de la mise à disposition de votre service. L'accès à vos données est protégé par une authentification forte, un grand nombre de contrôles d'accès et d'options d'autorisation Db2, le chiffrement en ligne (OTW, Over The Wire) et au repos, ainsi que pratiques en matière de sécurité et de conformité IBM applicables au développement et aux opérations. Le placement d'adresses IP sur liste blanche est proposé en option. Créez un cas de support IBM si vous voulez activer le placement d'adresses IP sur liste blanche.

### Procédure de connexion à un noeud final public :
{: #pub_endpt_steps}

La méthode la plus simple pour vous connecter à vos données est d'utiliser le nom d'hôte public que vous avez reçu dans votre courrier de bienvenue. Vous pouvez également vous procurer votre nom d'hôte et vos données d'identification de la manière suivante :

1. Connectez-vous à {{site.data.keyword.Db2_on_Cloud_short}}, puis cliquez sur votre instance de service.
2. Cliquez sur **Données d'identification pour le service**.
3. Cliquez sur **Nouvelles données d'identification**, puis sur **Ajouter**.
4. Une fois les données d'identification créées, sous la colonne `Actions`, cliquez sur **Afficher les données d'identification**.
5. Dans l'exemple de document JSON suivant, notez le contenu des zones hostname, password et username. Vous utiliserez ces trois éléments pour la connexion du noeud final public :

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

   ![Accès du réseau public à {{site.data.keyword.cloud_notm}}](images/public_connection.png)

## Connexion à un noeud final privé : IBM Cloud Service Endpoint
{: #priv_endpt}

Si une application est déployée sur votre compte {{site.data.keyword.cloud_notm}} et que vous voulez la connecter à votre base de données sans que le trafic de la base de données ne circule sur des réseaux publics, vous pouvez utiliser l'option **{{site.data.keyword.cloud_notm}} Service Endpoint** lorsque vous commandez votre base de données. Un nom d'hôte privé vous est fourni à la mise à disposition du service et vous ne pouvez vous y connecter qu'à partir de votre compte {{site.data.keyword.cloud_notm}}.  

Pour en savoir plus sur l'option {{site.data.keyword.cloud_notm}} Service Endpoint, voir [Service Endpoint : A propos](/docs/services/service-endpoint?topic=service-endpoint-about#about).


### Connexion à un noeud final privé avec IBM Cloud Service Endpoint
{: #priv_endpt_steps}

Les communications entre les réseaux et les noeuds finaux privés s'effectuent à l'aide du service {{site.data.keyword.cloud_notm}} Service Endpoint. Service Endpoint facilite le routage rapide et en toute sécurité du trafic réseau entre différents services {{site.data.keyword.cloud_notm}} et votre base de données via le circuit du réseau privé {{site.data.keyword.cloud_notm}}. Ce routage réseau garantit que vos données ne sortent jamais vers le réseau public Internet. 

Pour pouvoir utiliser Service Endpoint, votre compte {{site.data.keyword.cloud_notm}} doit être activé pour le routage et le transfert virtuels (VRF Virtual Routing and Forwarding). Pour activer VRF pour votre compte, voir [Enabling your account for using Service Endpoint by using IBM Cloud CLI](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

Une fois votre compte activé pour VRF et Service Endpoint activé, suivez les instructions fournies dans votre courrier de bienvenue.

C'est le moment de vous connecter à votre instance {{site.data.keyword.Db2_on_Cloud_short}} à partir de votre compte {{site.data.keyword.cloud_notm}} à l'aide de l'adresse de réseau privé fournie dans votre courrier de bienvenue.

## Connexion à un noeud final privé : réseau privé virtuel (VPN)
{: #vpn}

Si vous disposez d'une application déployée sur un réseau privé situé en dehors d'{{site.data.keyword.cloud_notm}} sans accès au réseau Internet public et que vous voulez la connecter à votre base de données via une connexion VPN (réseau privé virtuel), vous pouvez en faire la demande lorsque vous commandez le service ou en ouvrant un cas de support IBM. Les ingénieurs réseau IBM aideront vos ingénieurs réseau à configurer le tunnel VPN entre votre réseau privé et {{site.data.keyword.cloud_notm}}.

### Procédure de connexion à un noeud final privé à l'aide d'un réseau privé virtuel (VPN)
{: #priv_endpt_vpn_steps}

Pour établir une connexion VPN à votre base de données cloud derrière un noeud final public, [créez un cas de support {{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com/unifiedsupport/cases/add){:new_window} qui inclut les détails suivants :

* **Type de support** : Technique 
* **Catégorie** : Bases de données 
* **Offre** : sélectionnez votre instance {{site.data.keyword.Db2_on_Cloud_short}} 
* **Objet** : Demande de connexion VPN 
* **Description** : fournissez les informations requises suivantes
  * **Adresse d'homologue VPN côté client** (votre noeud final VPN) : `<IP Address>`
  * **Domaine de chiffrement côté client** (soyez précis concernant l'information requise – 10.0.0.0/8 ne fonctionne pas car l'adressage 10 est également utilisé dans les services de back end {{site.data.keyword.cloud_notm}}) : `<Domain>`
  * **Matériel & Version VPN côté client** : `<Hardware and Version number>`
  * **Contact VPN côté client** (nom et adresse électronique du contact technique) : 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Facultatif** (à modifier uniquement si les valeurs par défaut suivantes ne sont pas adaptées) :

  *Paramètres IKE/ISAKMP (Phase I)*

  * **Méthode de chiffrement** : IKEv1
  * **Chiffrement IKE / Algorithme de chiffrement** : AES-256
  * **Algorithme d'authentification** : SHA1
  * **DH-Group** : Group 5
  * **Durée de vie de l'association de sécurité (en secondes)** : 1d (86400 secondes)

  *Paramètres IPSEC (Phase II)*

  * **Chiffrement IPsec / Algorithme de chiffrement** : AES-256
  * **Algorithme d'authentification** : SHA1
  * **DH-Group** (si vous utilisez PF-Secrecy) : Group 5
  * **Durée de vie de l'association de sécurité (en secondes)** : 3600 secondes

Une fois votre demande reçue, les techniciens {{site.data.keyword.cloud_notm}} ouvrent les ports de pare-feu appropriés et placent en liste blanche l'adresse IP fournie. Vous êtes informé de l'avancée et de la résolution  de votre demande par le biais du ticket de cas de support {{site.data.keyword.cloud_notm}}.

![Accès du réseau public à {{site.data.keyword.cloud_notm}}](images/public_connection_vpn.png)
