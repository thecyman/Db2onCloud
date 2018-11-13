---

copyright:
  years: 2014, 2018
lastupdated: "2018-09-18"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Identity and Access management (IAM) sur IBM Cloud
{: #iam}

Identity and access management (IAM) vous permet d'authentifier de manière sécurisée les utilisateurs des services de plateforme et de contrôler l'accès aux ressources de façon cohérente au sein de la plateforme {{site.data.keyword.Bluemix_notm}}. Par exemple, avec une connexion unique à {{site.data.keyword.Bluemix_notm}} à l'aide de votre IBMid, vous avez accès à toutes vos consoles de maintenance et leurs applications sans qu'il soit nécessaire de vous connecter à chacune d'elles.
{: shortdesc}

## IAM est-il activé sur votre instance ?
{: #enabled}

Au bout d'un laps de temps, les instances de base de données gérées par {{site.data.keyword.Db2_on_Cloud_long}} sur {{site.data.keyword.Bluemix_notm}} pourront utiliser IAM pour le contrôle d'accès. Pour vérifier si IAM est activé sur votre instance, exécutez la requête suivante :

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

Si **IAM_ENABLED** renvoie la valeur 1, IAM est activé sur votre instance.

## Fonctions d'IBM Cloud IAM
{: #features}

Les fonctions IAM suivantes sont implémentées pour le service géré par {{site.data.keyword.Db2_on_Cloud_short}} avec deux types d'identités prises en charge :

**IBMid**

Pour pouvoir se connecter à une instance de service de base de données particulière, les utilisateurs disposant d'un IBMid doivent être ajoutés à chaque instance de service de base de données par l'administrateur de base de données via la console ou une API REST. Comme pour tout utilisateur ne disposant pas d'un IBMid, il est nécessaire de saisir un ID utilisateur pour l'instance de service de base de données lors de l'ajout de l'utilisateur avec un IBMid. Cet ID utilisateur doit être unique au sein de l'instance du service de base de données. Il s'agit également de l'ID d'autorisation (AUTH) au sein de la base de données. L'administrateur de base de données peut accorder ou révoquer des droits à partir de cet ID AUTH.

**ID de service**

Un ID de service identifie un service ou une application de la même façon qu'un ID utilisateur identifie un utilisateur. Les ID de service sont des ID pouvant être utilisés par les applications pour s'authentifier auprès d'un service IBM Cloud. Un ID de service représente une entité distincte de l'IBMid. Par conséquent, différents droits et permissions peuvent être accordés de manière spécifique à l'ID de service au sein de la base de données. Les ID de service n'ont pas de mots de passe. Une clé d'interface de programmation doit être créée pour chaque ID de service afin que ce dernier puisse se connecter à l'instance de service de base de données. Pour plus d'informations sur les ID de service, voir : [Introducing IBM Cloud IAM Service IDs and API Keys ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}.

## Connexions client et connexions utilisateur
{: #connect}

**Prérequis **: Db2 Client version 11.1 groupe de correctifs 3 et suivants.

Les méthodes suivantes peuvent être utilisées pour l'authentification IAM :

**Jeton d'accès**

Un jeton d'accès peut être obtenu auprès du service IAM directement par l'application via l'API REST à l'aide d'une clé d'interface de programmation. Pour plus d'informations, voir : [Getting an IBM Cloud IAM token by using an API key ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}. Le jeton d'accès a une période de validité par défaut de 60 minutes avant qu'il n'expire. Si le jeton a expiré, le serveur Db2 ne permet pas l'établissement de la connexion. La péremption du jeton n'est pas vérifiée une fois la connexion établie. Tout comme préalablement à l'intégration IAM, la connexion est maintenue jusqu'à ce que l'application se déconnecte ou que la connexion s'arrête pour d'autres raisons.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

Un jeton d'accès identifie un IBMid ou un ID de service auprès de la base de données. Le serveur de base de données vérifie la validité du jeton d'accès avant de l'accepter. Cette méthode est recommandée si l'application doit se connecter à plusieurs instances de service de base de données ou à d'autres instances de service {{site.data.keyword.Bluemix_notm}} car elle minimise la communication avec le service IAM pour valider le jeton d'accès.

**Clé d'interface de programmation**

Plusieurs clés d'interface de programmation peuvent être créées pour chaque utilisateur IBMid ou ID de service. Chaque clé d'interface de programmation est généralement créée pour une seule application. Cela permet à l'application de se connecter à l'instance de service de base de données dès lors que l'IBMid ou l'ID de service propriétaire est ajouté en tant qu'utilisateur à la même instance de service de base de données. La clé d'interface de programmation a les mêmes droits et permissions au sein de la base de données que l'IBMid ou l'ID de service propriétaire. Si une application ne doit plus être autorisée à se connecter à la base de données, la clé d'interface de programmation correspondante peut être retirée. La méthode d'authentification nécessite moins de changements dans l'application que l'utilisation d'un jeton d'accès car aucune interaction directe n'est nécessaire avec le service IAM. Pour plus d'informations sur la création et la gestion des clés d'interface de programmation, voir : [Managing user API keys ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}.

**IBMid/mot de passe**

L'IBMid/mot de passe peut être utilisé pour la connexion à la console et peut également être utilisé au sein de l'application de la même manière qu'un ID utilisateur/mot de passe. Il existe une exception lorsque l'IBMid est fédéré car un réacheminement est impossible vers la page de connexion de votre organisation. Toutefois, la méthode recommandée pour qu'une application puisse établir une connexion à l'instance de service de base de données est l'utilisation d'un jeton d'accès.

## Interfaces prises en charge
{: #sup-if}

Les interfaces client de base de données suivantes sont prises en charge :

* [ODBC](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC et CLPPLUS
{: #odbc-clpplus}

Pour qu'une application ODBC ou un client de ligne de commande (CLPPLUS) puisse se connecter un serveur Db2 à l'aide de l'authentification IAM, il est nécessaire de configurer au préalable un nom de source de données (DSN) dans un fichier de configuration `db2dsdriver.cfg` en exécutant la commande suivante :

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

Le fichier de configuration `db2dsdriver.cfg` est un fichier XML, situé généralement dans le répertoire `sqllib/cfg`, qui contient une liste des alias DSN et leurs propriétés.

Voici un exemple de fichier de configuration `db2dsdriver.cfg` indiquant les configurations qui sont utilisées pour établir une connexion à une instance de service de base de données. Le fichier de configuration fournit l'alias DSN, le nom de base de données, le nom d'hôte (ou l'adresse IP), ainsi que les valeurs de paramètre **Authentication** type et **SecurityTransportMode** :

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

* La chaîne de connexion ODBC peut contenir l'un des éléments suivants :

    **Jeton d'accès**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **Clé d'interface de programmation**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBMid/mot de passe**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    Pour ODBC, **AUTHENTICATION=GSSPLUGIN** peut être indiqué dans le fichier de configuration `db2dsdriver.cfg` ou dans la chaîne de connexion de l'application.

* La commande CLPPLUS connect peut contenir l'un des éléments suivants :

    **Jeton d'accès**

    Connect to the DSN alias (`@<data_source_name>`) and pass the access token by running the following command at the CLPPLUS command prompt or script:

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **Clé d'interface de programmation**

    Connect to the DSN alias (`@<data_source_name>`) with an API key by running the following command at the CLPPLUS command prompt or script:

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBMid/mot de passe**

    Connect to the DSN alias (`@<data_source_name>`) with an IBMid/password by running the following command at the CLPPLUS command prompt or script:

    `connect <IBMid>/<password>@<data_source_name>`

    Pour plus d'informations sur la connexion aux alias DSN avec CLPPLUS, voir : [DSN aliases in CLPPlus ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}.

### JDBC
{: #jdbc}

Le pilote JDBC Type 4 est pris en charge pour l'authentification IAM.

Voici des exemples qui indiquent les fragments de connexion pour les trois méthodes :

**Jeton d'accès**

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

**Clé d'interface de programmation**

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

**IBMid/mot de passe**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<user_ID>", "<password>" );
```

## Expérience utilisateur sur la console
{: #console-ux}

La page de connexion de la console de maintenance comporte une option qui vous permet de vous connecter avec votre IBMid et votre mot de passe. Un simple clic sur le bouton **Sign In via IBMid** et l'utilisateur est réacheminé sur la page de connexion IAM, où le mot de passe est saisi. Une fois l'authentification effectuée, l'utilisateur est redirigé vers la console. Pour qu'une telle connexion soit possible, il est nécessaire que l'utilisateur disposant d'un IBMid soit ajouté à chaque instance de service de base de données par l'administrateur de base de données via la console ou une API REST. Comme pour tout utilisateur ne disposant pas d'un IBMid, il est nécessaire de saisir un ID utilisateur pour l'instance de service de base de données lors de l'ajout de l'utilisateur avec un IBMid. Cet ID utilisateur doit être unique au sein de l'instance du service de base de données. Il s'agit également de l'ID d'autorisation (AUTH) au sein de la base de données. 

## Expérience API REST
{: #api}

L'API REST {{site.data.keyword.Db2_on_Cloud_short}} a été améliorée afin d'accepter également un jeton d'accès IAM pour les fonctions qui auparavant acceptaient un jeton d'accès généré par un service de base de données.

* Pour ajouter un nouvel utilisateur avec IBMid, exécutez l'exemple d'appel d'API suivant :

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  **Remarque **: La valeur `<userid>` pour `"id"` et `"ibmid"` ne doit pas être identique. Les deux ID différents ne sont liés en aucune manière.

* Pour migrer un utilisateur de base de données non IBMid existant (par exemple, `abcuser`) et en faire un utilisateur IBMid, commencez par supprimer l'ID utilisateur non IBMid en exécutant l'exemple d'appel API suivant :

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  Ensuite, ajoutez de nouveau l'utilisateur avec un IBMid identique au précédent ID utilisateur (`abcuser`) en exécutant l'exemple d'appel API suivant :

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Etant donné que l'ID utilisateur (`abcuser`) reste le même pour le nouvel IBMid de cet utilisateur, les droits de base de données accordés pour cet utilisateur demeurent inchangés. Si une liste d'utilisateurs de base de données non IBMid existants doit être migrée afin d'en faire des utilisateurs IBMid, vous devez exécuter la précédente paire d'appels API pour chaque utilisateur.

* Pour ajouter un grand nombre de nouveaux utilisateurs IBMid en une seule opération, créez un fichier de traitement par lots répertoriant les exemples d'appels API suivants, un pour chaque utilisateur :

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

Pour plus de détails sur l'API de votre service, voir : [{{site.data.keyword.Db2_on_Cloud_short}} REST API ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://ibm.biz/db2oc_api){:new_window}.

## Fédération IBMid
{: #fed}

Pour utiliser votre propre fournisseur d'identité, LDAP par exemple, vous devez d'abord fédérer votre serveur LDAP avec IBMid. Pour les instructions relatives à la fédération de votre serveur LDAP avec IBMid, voir : [IBMid Enterprise Federation Adoption Guide ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}. Une fois la fédération IBMid effectuée et dès lors que les utilisateurs autorisés sont ajoutés à l'instance de service de base de données par l'administrateur de base de données, ces utilisateurs peuvent se connecter à la console à l'aide de leur ID utilisateur et mot de passe d'entreprise. Ces utilisateurs peuvent aussi utiliser un jeton d'accès ou une clé d'interface de programmation qui représente leur ID utilisateur pour se connecter à l'instance de service de base de données via l'une des interfaces client de base de données prises en charge.

## Restrictions
{: #restrictions}

Voici quelques restrictions concernant l'authentification IAM :

* L'authentification IAM pour un client Db2 qui se connecte à un serveur Db2 n'est possible que sur une connexion SSL.
* La fédération IBMid est prise en charge pour autoriser l'utilisation d'un portail ou serveur de gestion des utilisateurs personnalisé à des fins d'authentification. Cette prise en charge n'inclut pas la fédération de groupe.
* L'authentification IAM pour la fédération de base de données n'est pas pris en charge.
* L'exécution de commandes IDA et UDX via des CLPPlus n'est pas prise en charge.
* Le pilote JDBC Type 2 n'est pas pris en charge.




