---

copyright:
  years: 2014, 2019
lastupdated: "2019-05-23"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:javascript: #javascript .ph data-hd-programlang='javascript'}
{:java: #java .ph data-hd-programlang='java'}
{:ruby: #ruby .ph data-hd-programlang='ruby'}
{:php: #php .ph data-hd-programlang='php'}
{:python: #python .ph data-hd-programlang='python'}
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Esercitazione introduttiva
{: #getting-started}

{{site.data.keyword.Db2_on_Cloud_long}} è un database SQL di cui viene eseguito il provisioning nel cloud per te. Puoi utilizzare {{site.data.keyword.Db2_on_Cloud_short}} come useresti qualsiasi software database ma senza dover sostenere l'onore del tempo e dei costi necessari per la configurazione dell'hardware o l'installazione e la manutenzione del software. 
{: shortdesc}

Crea le credenziali. Per chi non ha esperienza con IBM Cloud, dopo la creazione del servizio è necessario creare un nome utente e una password facendo clic sul pulsante **Create Credentials** quando avvii il servizio. Tecnicamente, puoi accedere alla console web senza credenziali, ma hai bisogno di nome utente e password per utilizzare molti degli strumenti Db2.
{: important}

Puoi anche installare un database db2 locale utilizzando il [download di Db2 Developer Edition gratuito](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:external}. Installa rapidamente una Developer Edition di Db2 pronta per l'uso all'interno di un contenitore Docker (Docker non richiesto; installa automaticamente qualsiasi componente necessario). 

## Interfacce
{: #interfaces}

Puoi lavorare con il tuo database {{site.data.keyword.Db2_on_Cloud_short}} nei seguenti modi:
{: shortdesc}

   * Console web {{site.data.keyword.Db2_on_Cloud_short}}
   * API REST
   * Connetti le applicazioni o i tuoi strumenti preferiti dal tuo computer locale
   * Usa {{site.data.keyword.Db2_on_Cloud_short}} come origine dati per le tue applicazioni o i tuoi servizi {{site.data.keyword.Bluemix_notm}}

### Console web di Db2 on Cloud
{: #web_console}

La console web fornisce un'interfaccia grafica per tutto quello che ti serve per utilizzare il tuo database, tra cui: funzionalità di carico, un editor SQL, dei download di driver e altro ancora.
{: shortdesc}

<!-- ![View of Db2 on Cloud web console dashboard page](images/console_v2.png) -->
<!-- ![View of {{site.data.keyword.dashdbshort_notm}} web console dashboard page](images/console_v2.jpg) -->

<!-- Click the link to take a tour of the Db2 web console: [General tour](http://ibm.biz/dashdb-general-quick-tour){:external}. -->

Puoi accedere alla tua console web {{site.data.keyword.Db2_on_Cloud_short}} nei seguenti modi:
   * Dal tuo dashboard {{site.data.keyword.Bluemix_notm}} - puoi aprire la console web dalla pagina Dettagli del servizio per il tuo servizio {{site.data.keyword.Db2_on_Cloud_long_notm}}.
   * URL diretto - puoi mettere tra i preferiti l'URL della console web per il tuo servizio {{site.data.keyword.Db2_on_Cloud_short}}.

<!-- ###REST APIs
{: #apis}

With Db2 Warehouse plans, you can perform tasks related to file management, loading data, and running R scripts by using the [Db2 Warehouse REST API](http://ibm.biz/dashdb-api){:external}.
{: shortdesc} -->

### Installazione dei driver e dei client della riga di comando Db2 sul tuo computer
{: #connect_apps}

Nella maggior parte dei casi, gli utenti tendono ad utilizzare solo l'API REST o a installare i driver per un framework, ad esempio con il comando `pip` di Python. 
{: shortdesc}

Per installare i pacchetti di driver Python per MacOS, devi utilizzare il comando `pip` con l'opzione `--no-cache-dir`. Per istruzioni dettagliate, vedi: [Python support for IBM DB2 and IBM Informix](https://ibm.biz/db2-drivers-python){:external}.
{: note}

Se stai eseguendo del lavoro di data science con Python, o vuoi supporto per frame di dati, analisi nel database o utilizzo di Watson Studio, potresti voler usare il seguente driver alternativo, che pone l'accento sul supporto per una gamma di funzioni di data science: [ibmdbpy 0.1.5](https://pypi.org/project/ibmdbpy/){:external}.
{: note}

<!-- Drivers on site are broken so taking out this one -Simon. 1. Download the [driver package](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package.html){:external} from the Connection info page of the {{site.data.keyword.Db2_on_Cloud_short}} web console.-->

Per installare i driver di framework Python o Node.js, fai clic su uno dei seguenti link:
- [Driver Python](https://ibm.biz/db2-drivers-python){:external}
- [Driver Node.js](https://ibm.biz/db2-drivers-node){:external}

Per installare l'ORM Node.js denominato Sequelize, fai clic sul seguente link:
[Sequelize](https://github.com/ibmdb/sequelize){:external}
{: note}

Per ulteriori opzioni di installazione del driver, tra cui Java, Go, Jupyter Notebook, Ruby, PHP e altro, fai clic sul seguente link: 

- [ibmdb](https://github.com/ibmdb){:external}

Presumendo che hai già installato i driver di framework, puoi tralasciare i seguenti passi. Tuttavia, i power user potrebbero voler utilizzare il client della riga di comando Db2 per gestire i propri database e utilizzare i comandi Db2. Inoltre, alcune applicazioni ODBC o JDBC possono trarre vantaggio da un'installazione generale dei driver Db2. In questo caso, effettua le operazioni riportate di seguito:

1. [Installa il pacchetto driver](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_install.html){:external} sul computer dove sono in esecuzione le tue applicazioni o i tuoi strumenti.
2. [Configura i file del driver](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:external} per il tuo database {{site.data.keyword.Db2_on_Cloud_short}}.

### Usa Db2 on Cloud come origine dati per le tue applicazioni o i tuoi servizi {{site.data.keyword.Bluemix_notm}}
{: #data_src}

Le applicazioni ospitate su {{site.data.keyword.Bluemix_notm}} possono connettersi al tuo database {{site.data.keyword.Db2_on_Cloud_short}} nello stesso modo in cui le tue applicazioni locali si connettono al tuo database {{site.data.keyword.Db2_on_Cloud_short}}.
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

## Esempi
{: #samples}

Sono qui riportati dei link ad esempi che illustrano come stabilire una connessione al tuo database {{site.data.keyword.Db2_on_Cloud_short}} da applicazioni in linguaggi differenti:
{: shortdesc}

   * [.NET](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:external}
<!-- * [JAVA](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_java.html){:external} -->
   * [JDBC](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:external}
<!-- * [Node.js](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_nodejs.html){:external} -->
   * [PHP](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:external}
<!-- * [Python](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_python.html){:external} -->
<!-- * [{{site.data.keyword.Db2_on_Cloud_short}} samples on GitHub](https://github.com/IBM-Bluemix/dashdb-nodejs-helloworld){:external} -->

## Video: Introduzione a Db2 on Cloud
{: #intro_vid}

Guarda questo video per vedere un'introduzione a {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer1" title="Introduzione a {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/F_ylk44_WOg?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Video: utilizzo dell'API REST per comunicare con Db2 on Cloud
{: #vid_api}

Guarda questo video per vedere i passi necessari per utilizzare un'API RESTful per comunicare con {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer2" title="Utilizzo dell'API RESTful per comunicare con {{site.data.keyword.Db2_on_Cloud_short}}" type="text/html" width="640" height="390" src="//www.youtube.com/embed/PSNBDwgf9ts?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>

## Video: integrazione con i notebook Jupyter
{: #cognos_vid}

Guarda questo video per vedere come integrare i notebook Jupyter con {{site.data.keyword.Db2_on_Cloud_short}}.

<iframe class="embed-responsive-item" id="youtubeplayer3" title="Integrazione dei notebook Jupyter" type="text/html" width="640" height="390" src="//www.youtube.com/embed/bNfH0Wzx3is?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe>


