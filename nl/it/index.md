---

copyright:
  years: 2014, 2017
lastupdated: "2017-06-21"

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:pre: .pre}

#Introduzione a Db2 on Cloud (precedentemente dashDB for Transactions)
{: #getting_started_db2oncloud}

{{site.data.keyword.Db2_on_Cloud_long}} è un database SQL di cui viene eseguito il provisioning nel cloud per te. Puoi utilizzare {{site.data.keyword.Db2_on_Cloud_short}} come useresti qualsiasi software database ma senza dover sostenere il carico di lavoro e i costi necessari per la configurazione dell'hardware o l'installazione e la manutenzione del software.
{: shortdesc}

##Interfacce
{: #interfaces}

Puoi lavorare con il tuo database {{site.data.keyword.Db2_on_Cloud_short}} nei seguenti modi:
{: shortdesc}

   * Console web {{site.data.keyword.Db2_on_Cloud_short}}
<!--   * REST APIs -->
   * Connetti le applicazioni o i tuoi strumenti preferiti dal tuo computer locale
   * Usi {{site.data.keyword.Db2_on_Cloud_short}} come un'origine dati per le tue applicazioni o i tuoi servizi Bluemix

###Console web Db2 on Cloud
{: #web_console}

La console web fornisce un'interfaccia grafica per tutto quello che ti serve per utilizzare il tuo database, tra cui: funzionalità di carico, un editor SQL, dei download di driver e altro ancora.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-general-quick-tour "External link icon"){:new_window}. -->

Puoi accedere alla tua console web {{site.data.keyword.Db2_on_Cloud_short}} nei seguenti modi:
   * Dal tuo dashboard {{site.data.keyword.Bluemix_notm}} - puoi aprire la console web dalla pagina Dettagli del servizio per il tuo servizio {{site.data.keyword.Db2_on_Cloud_long_notm}}.
   * URL diretto - puoi mettere tra i preferiti l'URL della console web per il tuo servizio {{site.data.keyword.Db2_on_Cloud_short}}.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://ibm.biz/dashdb-api){:new_window}.
{: shortdesc} -->

###Connetti le applicazioni o i tuoi strumenti preferiti dal tuo computer locale
{: #connect_apps}

Configura il tuo ambiente locale per stabilire una connessione al tuo database {{site.data.keyword.Db2_on_Cloud_short}} completando la seguente procedura:
{: shortdesc}

1. Scarica il [pacchetto di driver ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html "Icona di link esterno"){:new_window} dalla pagina di informazioni sulla connessione della console web {{site.data.keyword.Db2_on_Cloud_short}}.
2. [Installa il pacchetto di driver ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html "Icona di link esterno"){:new_window} sul computer dove sono in esecuzione le tue applicazioni e i tuoi strumenti.
3. [Configura i file di driver ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html "Icona di link esterno"){:new_window} per il tuo database {{site.data.keyword.Db2_on_Cloud_short}}.

###Usa Db2 on Cloud come origine dati per le tue applicazioni o i tuoi servizi Bluemix
{: #data_src}

Le applicazioni ospitate su {{site.data.keyword.Bluemix_notm}} possono connettersi al tuo database {{site.data.keyword.Db2_on_Cloud_short}} nello stesso identico modo in cui le tue applicazioni locali si connettono al tuo database {{site.data.keyword.Db2_on_Cloud_short}}.
{: shortdesc}

Quando le tue applicazioni utilizzano la piattaforma {{site.data.keyword.Bluemix_notm}}, puoi usare la variabile di ambiente `VCAP _SERVICES` per semplificare l'attività di specifica dei dettagli e delle credenziali del database:
1. Sul tuo dashboard {{site.data.keyword.Bluemix_notm}}, nella scheda **Connessioni** della pagina Dettagli del servizio per il tuo servizio {{site.data.keyword.Db2_on_Cloud_long_notm}}, fai clic sul pulsante **Crea connessione**.
2. Seleziona l'applicazione {{site.data.keyword.Bluemix_notm}} da utilizzare con il tuo database {{site.data.keyword.Db2_on_Cloud_short}} come un'origine dati e fai quindi clic sul pulsante **Connetti**.
3. Aggiorna il tuo codice applicativo per richiamare i dettagli e le credenziali del database dalla variabile di ambiente `VCAP_SERVICES`:

    **Esempio senza `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $database    = "BLUDB";         # Ottieni questi dettagli del database dalla
    $hostname    = "<Host-name>";   # pagina Connetti della console
    $port        = 50000;           # web Db2 on Cloud.
    $user        = "<User-ID >";    #
    $password    = "<Password>";    #
    $dsn         = "DATABASE=$database;" .
                   "HOSTNAME=$hostname;" .
                   "PORT=$port;" .
                   "PROTOCOL=TCPIP;" .
                   "UID=$user;" .
                   "PWD=$password;";

    $conn_string = $driver . $dsn;

    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

    **Esempio con `VCAP_SERVICES`**

    ```php
    <?php
    $driver      = "DRIVER={IBM DB2 ODBC DRIVER};";

    $vcap        = json_decode( getenv( "VCAP_SERVICES" ), true );
    $dsn         = $vcap[ "dashDB" ][0][ "credentials" ][ "dsn" ];

    $conn_string = $driver . $dsn;
                                   
    $conn        = db2_connect( $conn_string, "", "" );
    ?>
    ```

##Esempi
{: #samples}

Sono qui riportati dei link ad esempi che illustrano come stabilire una connessione al tuo database {{site.data.keyword.Db2_on_Cloud_short}} da applicazioni in linguaggi differenti:
{: shortdesc}

   * [.NET ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html "Icona di link esterno"){:new_window}
<!-- * [JAVA ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html "External link icon"){:new_window} -->
   * [JDBC ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html "Icona di link esterno"){:new_window}
<!-- * [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html "External link icon"){:new_window} -->
   * [PHP ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html "Icona di link esterno"){:new_window}
<!-- * [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html "External link icon"){:new_window} -->
   * [Esempi {{site.data.keyword.Db2_on_Cloud_short}} su GitHub ![Icona di link esterno](../../icons/launch-glyph.svg "Icona di link esterno")](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld "Icona di link esterno"){:new_window}


