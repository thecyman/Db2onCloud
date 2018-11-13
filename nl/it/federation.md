---

copyright:
  years: 2014, 2018
lastupdated: "2018-10-26"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

# Virtualizzazione dei dati (federazione)
{: #overview}

La virtualizzazione dei dati Db2 (nota anche come federazione) è supportata da {{site.data.keyword.Db2_on_Cloud_short}}. La virtualizzazione dei dati ti fornisce l'accesso con una singola query a tutti i dati presenti su più database distribuiti in qualsiasi punto della tua organizzazione. Puoi accedere ai dati che si trovano su una qualsiasi delle tue origini dati Db2 o Informix, sia nel cloud che in loco. 
{: shortdesc}

Questa funzione è supportata su tutte le versioni di {{site.data.keyword.Db2_on_Cloud_short}}, ad eccezione del piano Lite gratuito. Tuttavia, puoi utilizzare il piano Lite come destinazione da cui potrai estrarre i dati.

## Casi di utilizzo
{: #use_cases}

### Consolidamenti delle origini dati

Federando le tue origini dati che si trovano sia nel cloud che in loco in qualsiasi punto della tua organizzazione, i tuoi dati virtualizzati sembrano essere richiamati da un'unica origine. La virtualizzazione dei dati elimina il processo di migrazione dei dati particolarmente oneroso e costoso, offrendoti la possibilità di analizzare tutti i tuoi dati in modo efficiente ed economico.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Collegamento a Db2 Warehouse on Cloud

Gli utenti dei prodotti della famiglia Db2 possono federare i dati dai database {{site.data.keyword.Db2_on_Cloud_short}} e {{site.data.keyword.dashdbshort_notm}}. Da una comune interfaccia per accedere ai dati, puoi aggiungere, eseguire query e analizzare facilmente i dati senza complessi processi ETL e senza alcun codice aggiuntivo.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### Dati partizionati su più server

Ci sono delle volte in cui potresti scegliere di partizionare (frammentare) i tuoi dati. Con le funzionalità di federazione, è possibile eseguire query dei dati partizionati mediante un'interfaccia unificata. La federazione ti offre la possibilità di bilanciare meglio i tuoi carichi di lavoro, ridimensionare parti specifiche di un'applicazione e creare microservizi che lavorano insieme. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### Aumento della capacità del database oltre i limiti stabiliti

La federazione ti dà la possibilità di aumentare la capacità di un database installato in loco mediante la federazione con un database sul cloud. In questo caso, la virtualizzazione dei dati è un'ottima opzione se il tuo database in loco sta esaurendo lo spazio di archiviazione. L'aumento della capacità di un database mediante la federazione è utile per il nuovo sviluppo perché gli sviluppatori non hanno bisogno di modificare un database già in produzione. Puoi anche creare una federazione tra due database {{site.data.keyword.Db2_on_Cloud_short}} per aumentare la capacità del database oltre i limiti attuali del piano Flex.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## Introduzione
{: #getting_started}

I seguenti passi sono un esempio di come puoi federare le tue diverse origini dati per sembrare come se i dati fossero richiamati da una singola origine. Il seguente esempio illustra la federazione di due database {{site.data.keyword.Db2_on_Cloud_short}}:

### Nella macchina di destinazione Db2 on Cloud

Nome host: targetdotcom

1. Crea una tabella `testdata` nello schema `admin2`.

2. Dalla console di {{site.data.keyword.Db2_on_Cloud_short}}, carica i dati nella tabella `testdata` come utente `admin2` con la password `YYYY`.

<!-- ### On a client machine of the target

1. Catalog the target machine:<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   For example:<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. Catalog the database on fedS:<br/>
   `db2 catalog db bludb as <db_name> at node <node_name>`

   For example:<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. Connect to the database on fedS:<br/>
   `db2 connect to <catalog_db_name> user <admin_user> using '<admin_password>'`

   For example:<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. Create a wrapper on fedS:<br/>
   `db2 "create wrapper drda"`

5. Create a server to talk to the target machine:<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   For example:<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. Create the user mapping for admin2:<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   For example:<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. Create a nickname for the database:<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   For example:<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### On the Db2 on Cloud source machine

1. Test that you can pull data from the target server:<br/>
   `db2 "select * from <nickname>"`

   For example:<br/>
   `db2 "select * from ntest1"`
-->

### Su una macchina Db2 on Cloud che viene utilizzata come un'origine di federazione

Dalla console di {{site.data.keyword.Db2_on_Cloud_short}}:

1. Crea un server per comunicare con la macchina di destinazione:<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   Ad esempio:<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. Crea l'associazione utente per admin2:<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   Ad esempio:<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. Crea un soprannome per il database:<br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   Ad esempio:<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. Verifica di poter estrarre i dati dal server di destinazione:<br/>
   `select * from <nickname>`

   Ad esempio:<br/>
   `select * from ntest1`

## Ulteriori informazioni

Per ulteriori informazioni sulla virtualizzazione dei dati (federazione), vedi: [Federation ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}.

Per impostazione predefinita, {{site.data.keyword.Db2_on_Cloud_short}} supporta Informix e Db2 (inclusi Db2 in loco e Warehouse Db2). Potrebbe essere necessario installare il supporto per alcune origini dati dal supporto IBM su richiesta. Per informazioni sulle origini dati supportate dalla federazione, vedi: [Federation Supported Data Sources ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}.

