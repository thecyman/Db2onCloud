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

# Identity and access management (IAM) su IBM Cloud
{: #iam}

Identity and access management (IAM) ti abilita ad autenticare in modo sicuro gli utenti per i servizi della piattaforma e controllare l'accesso alle risorse in modo coerente alla piattaforma {{site.data.keyword.Bluemix_notm}}. Ad esempio, con un solo accesso a {{site.data.keyword.Bluemix_notm}} con il tuo ID IBM, hai accesso a tutte le console del servizio e alle loro applicazioni senza dover accedere ad ognuna di esse separatamente.
{: shortdesc}

## IAM è abilitato sulla tua istanza?
{: #enabled}

In poco tempo, le istanze del database gestite da {{site.data.keyword.Db2_on_Cloud_long}} su {{site.data.keyword.Bluemix_notm}} saranno abilitate ad utilizzare IAM per il controllo dell'accesso. Per controllare se IAM è abilitato sulla tua istanza, esegui la seguente query:

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

Se il valore restituito per **IAM_ENABLED** è 1, IAM è abilitato sulla tua istanza.

## Funzioni di IAM IBM Cloud
{: #features}

Le seguenti funzioni IAM sono implementate per il servizio gestito da {{site.data.keyword.Db2_on_Cloud_short}} con due tipi di identità supportate:

**ID IBM**

Gli utenti con un ID IBM devono essere aggiunti a ogni istanza del servizio database dall'amministratore del database tramite la console o l'API REST prima che questi utenti possano collegarsi a quella particolare istanza del servizio database. Proprio come per un utente non ID IBM, un ID utente per l'istanza del servizio database deve essere immesso nello stesso momento in cui viene aggiunto l'utente ID IBM. Questo ID utente deve essere univoco all'interno dell'istanza del servizio database. Questo ID utente è anche l'ID di autorizzazione (AUTH) all'interno del database. L'amministratore del database può concedere e revocare le autorizzazioni basate sull'ID AUTH.

**ID servizio**

Un ID identifica un servizio o un'applicazione in modo simile a come un ID utente identifica un utente. Gli ID servizio sono gli ID che possono essere utilizzati dalle applicazioni per l'autenticazione a un servizio IBM Cloud. Un ID servizio rappresenta un'entità separata dall'ID IBM di appartenenza. Pertanto, autorità e autorizzazioni diverse possono essere concesse in modo specifico all'ID servizio all'interno del database. Gli ID servizio non hanno password. Deve essere creata una chiave API per ogni ID servizio per l'ID da collegare all'istanza del servizio database. Per ulteriori informazioni sugli ID servizio, consulta: [Introducing IBM Cloud IAM Service IDs and API Keys ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}.

## Connessioni client e accessi utente
{: #connect_user}

**Prerequisito**: Client Db2 V11.1 FP3 e successive.

I seguenti metodi possono essere utilizzati per l'autenticazione IAM:

**Token di accesso**

Puoi ottenere un token di accesso dal servizio IAM direttamente dall'applicazione tramite l'API REST utilizzando una chiave API. Per ulteriori informazioni, consulta: [Getting an IBM Cloud IAM token by using an API key ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}. Il token di accesso ha un periodo di validità predefinito di 60 minuti prima della scadenza. Se il token è scaduto, il server Db2 non consentirà di stabilire la connessione. Non viene controllata la scadenza del token dopo che la connessione è stata stabilita. Così come era prima dell'integrazione di IAM, la connessione rimarrà in essere fino a quando l'applicazione non si scollega o viene terminata a causa di altre ragioni.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

Un token di accesso identifica un utente ID IBM o un ID servizio al database. Il server del database verifica la validità del token di accesso prima di accettarlo. Questo è il metodo migliore se l'applicazione deve connettersi a più di un'istanza del servizio database o ad altre istanze del sevizio {{site.data.keyword.Bluemix_notm}} perché minimizza la comunicazione al servizio IAM per convalidare il token di accesso.

**Chiave API**

Possono essere create più chiavi per ogni ID servizio o utente ID IBM. Ogni chiave API viene normalmente creata per una singola applicazione. Consente all'applicazione di connettersi all'istanza del servizio database fino a quando l'ID IBM di appartenenza o l'ID servizio viene aggiunto come un utente alla stessa istanza del servizio database. La chiave API ha le stesse autorizzazioni all'interno del database come l'ID servizio o l'ID IBM di appartenenza. Se un'applicazione non deve più essere consentita per connettersi al database, la chiave API corrispondente può essere rimossa. Questo metodo di autenticazione richiede meno modifiche nell'applicazione rispetto all'utilizzo di un token di accesso poiché non richiede un'interazione diretta con il servizio IAM. Per ulteriori informazioni sulla creazione e la gestione delle chiavi API, consulta: [Gestione delle chiavi API utente ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}.

**ID IBM/password**

Puoi utilizzare l'ID IBM e la password per accedere alla console e anche all'interno dell'applicazione negli stessi modi in cui sono consentiti l'ID utente e la password. Si verifica un'eccezione quando l'ID IBM è federato perché non è possibile eseguire un reindirizzamento alla pagina di accesso della tua organizzazione. Tuttavia, il metodo consigliato per un'applicazione di stabilire una connessione all'istanza del servizio database è quello di utilizzare un token di accesso.

## Interfacce supportate
{: #sup-if}

Sono supportate le seguenti interfacce client del database:

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC, CLP e CLPPLUS
{: #odbc-clpplus}

Per un'applicazione ODBC o un client riga di comando (CLP, CLPPLUS) per connettersi a un server Db2 utilizzando l'autenticazione IAM, deve essere prima configurato un nome dell'origine dati (DSN) in un file di configurazione `db2dsdriver.cfg`, immettendo il seguente comando:

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

Il file di configurazione `db2dsdriver.cfg` è un file XML, normalmente ubicato nella directory `sqllib/cfg`, che contiene un elenco di alias DSN e le relative proprietà.

Il seguente esempio di un file di configurazione di `db2dsdriver.cfg` mostra le configurazioni utilizzate per stabilire una connessione a un'istanza del servizio database. Il file di configurazione fornisce l'alias DSN, il nome del database, il nome host (o l'indirizzo IP) e il tipo **Authentication** e i valori del parametro **SecurityTransportMode**:

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

* La stringa di connessione ODBC può contenere uno dei seguenti:

    **Token di accesso**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **Chiave API**

    `DSN=<dsn>;APIKEY=<api_key>`

    **ID IBM/password**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    Per ODBC, può essere specificato **AUTHENTICATION=GSSPLUGIN** nel file di configurazione `db2dsdriver.cfg` o nella stringa di connessione dell'applicazione.

* L'istruzione CLP CONNECT può contenere uno dei seguenti:

    **Token di accesso**

    Collegati al server database `<database_server_name>` e passa il token di accesso immettendo il seguente comando allo script o prompt del comando CLP:

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **Chiave API**

    Collegati al server database `<database_server_name>` con una chiave API immettendo il seguente comando allo script o prompt del comando CLP:

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **ID IBM/password**

    Collegati al server database `<database_server_name>` con un ID IBM/password immettendo il seguente comando allo script o prompt del comando CLP:

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    Per ulteriori dettagli sulla connessione a un server database con CLP, consulta: [CONNECT (type 2) statement ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}. 

* L'istruzione CLPPLUS CONNECT può contenere uno dei seguenti:

    **Token di accesso**

    Connettiti all'alias DSN (`@<data_source_name>`) e passa il token di accesso immettendo il seguente comando allo script o prompt del comando CLPPLUS:

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **Chiave API**

    Connettiti all'alias DSN (`@<data_source_name>`) con una chiave API immettendo il seguente comando allo script o prompt del comando CLPPLUS:

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **ID IBM/password**

    Connettiti all'alias DSN (`@<data_source_name>`) con un ID IBM/password immettendo il seguente comando allo script o prompt del comando CLPPLUS:

    `connect <IBMid>/<password>@<data_source_name>`

    Per ulteriori dettagli sulla connessione agli alias DSN con CLPPLUS, consulta: [DSN aliases in CLPPlus ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}.

### JDBC
{: #jdbc}

Il driver JDBC  di tipo 4 è supportato per l'autenticazione IAM.

I seguenti esempi mostrano i frammenti di connessione per i tre metodi:

**Token di accesso**

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

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**Chiave API**

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

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apikey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**ID IBM/password**

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

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## Esperienza utente console
{: #console-ux}

La pagina di accesso della console di servizio ha l'opzione di accedere con i tuoi ID IBM e password. Dopo aver fatto clic sul pulsante **Sign In via IBMid**, l'utente viene indirizzato alla pagina di accesso IAM, su cui viene immessa la password. Quando l'autenticazione è stata completata, l'utente viene reindirizzato nuovamente alla console. Prima di eseguire correttamente l'accesso, l'ID IBM deve essere aggiunto a ogni istanza del servizio database dall'amministratore del database tramite la console o l'API REST. Proprio come per un utente non ID IBM, un ID utente per l'istanza del servizio database deve essere immesso nello stesso momento in cui viene aggiunto l'utente ID IBM. L'ID utente deve essere univoco all'interno dell'istanza del servizio database. Questo ID utente è anche l'ID di autorizzazione (AUTH) all'interno del database.

## Esperienza API REST
{: #api}

L'API REST {{site.data.keyword.Db2_on_Cloud_short}} è stata migliorata per accettare anche un token di accesso IAM per le funzioni che in precedenza accettavano un token di accesso generato dal servizio database.

* Per aggiungere un nuovo utente ID IBM, esegui la seguente chiamata API di esempio:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Il valore `<userid>` per `"id"` e `"ibmid"` non deve essere lo stesso. I due ID diversi non sono collegati in alcun modo.
  {: note}

* Per migrare un utente del database non ID IBM esistente (ad esempio, `abcuser`) e farne un utente ID IBM, elimina prima l'ID utente non ID IBM eseguendo la seguente chiamata API di esempio:

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  Successivamente, riaggiungi l'utente con un ID IBM che è lo stesso dell'ID utente precedente (`abcuser`) eseguendo la seguente chiamata API di esempio:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Poiché l'ID utente (`abcuser`) rimane lo stesso per il nuovo ID IBM per tale utente, le autorizzazioni database concesse per l'utente restano invariate. Se un elenco di utenti del database non ID IBM esistenti deve essere migrato per renderli utenti ID IBM, devi eseguire la coppia precedente di chiamate API per ogni utente.

* Per aggiungere molti nuovi utenti ID IBM contemporaneamente, crea un file batch che elenca le seguenti chiamate API di esempio, una per ogni utente:

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

Per ulteriori dettagli sull'API del tuo servizio, consulta: [{{site.data.keyword.Db2_on_Cloud_short}} REST API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](http://ibm.biz/db2oc_api){:new_window}.

## Federazione ID IBM
{: #fed_ibmid}

Per utilizzare il tuo provider di identità come ad esempio LDAP, devi prima federare il tuo server LDAP con l'ID IBM. Per istruzioni su come federare il server LDAP con l'ID IBM, consulta: [IBMid Enterprise Federation Adoption Guide ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}. Dopo che la federazione dell'ID IBM è stata completata e gli utenti consentiti sono stati aggiunti all'istanza del servizio database dall'amministratore del database, questi utenti possono accedere alla console con i loro ID utente e password aziendali. In alternativa, questi utenti possono utilizzare un token di accesso o una chiave API che rappresenta il proprio ID utente per connettersi all'istanza del servizio database tramite una delle interfacce client del database supportate.

## Limitazioni
{: #restrictions}

Le seguenti sono le limitazioni che riguardano l'autenticazione IAM:

* L'autenticazione IAM per un client Db2 che si collega a un server Db2 è supportata solo su una connessione SSL.
* La federazione dell'ID IBM è supportata per consentire l'utilizzo di un portale o di un server di gestione utenti personalizzato per l'autenticazione. Tale supporto non include alcuna federazione di gruppo.
* L'autenticazione IAM per la federazione del database non è supportata.
* L'esecuzione dei comandi delle estensioni definite dall'utente (UDX) e IDA tramite CLPPlus non è supportata.
* Il driver JDBC di tipo 2 non è supportato.




