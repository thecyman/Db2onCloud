---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

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

# Migrazione dei dati su IBM Cloud
{: #migration}

Puoi caricare i dati da un file di dati in un formato delimitato (CSV o TXT) situato su una rete locale o in un archivio oggetti (Amazon S3 o IBM Cloud Object Storage) su {{site.data.keyword.Db2_on_Cloud_long}}. Puoi anche migrare i tuoi dati da un sistema installato in loco.
{: shortdesc}

## Caricamento dei dati dall'archivio oggetti
{: #cos}

Per caricare i dati da Amazon S3, seleziona uno dei seguenti metodi:
  * Console web {{site.data.keyword.Db2_on_Cloud_short}}. **Load > Amazon S3**. 
  * Direttamente dalle tabelle esterne. Il seguente è un esempio di istruzione SQL:

    ```
    INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
        (CCSID 1208 s3('s3.amazonaws.com', 
        '<S3-access-key-ID>',
        '<S3-secret-access-key>', 
        '<my_bucket>'
           )
      )      
    ```

Per caricare i dati da IBM Cloud Object Storage utilizzando direttamente tabelle esterne, puoi utilizzare la seguente istruzione SQL di esempio:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )      
```

Per IBM Cloud Object Storage, per creare le credenziali HMAC durante la creazione di nuove credenziali di servizio, specifica {"HMAC:true"} nel campo *Aggiungi parametri di configurazione inline*.
{: note}

## Migrazione dei dati dal sistema installato in loco
{: #onprem}

Per migrare i tuoi dati da un sistema installato in loco, scegli uno dei seguenti metodi in base alla dimensione del tuo dataset:
* Meno di 25 TB di dati: [CLI IBM Lift](#lift)
* 25 o più TB di dati: [IBM Cloud Mass Data Migration](#mdms)

### CLI Lift
{: #lift}

La CLI Lift è un'applicazione che puoi utilizzare gratuitamente per migrare i tuoi dati su {{site.data.keyword.Bluemix_notm}} dalle diverse origini dati elencate nella Tabella 1. 

| Database di destinazione su IBM Cloud | Origine dati |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Database Oracle |
|                              | Microsoft SQL Server |
|                              | Formato di file CSV |
{: caption="Tabella 1. Origini dati di migrazione" caption-side="top"}

Per scaricare e installare la CLI Lift, vedi: [Download Lift CLI ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#download){:new_window}.

Per istruzioni dettagliate sulla migrazione dei tuoi dati su {{site.data.keyword.Bluemix_notm}} mediante la CLI Lift, vedi: [Migrate data to {{site.data.keyword.Db2_on_Cloud_long_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#docs){:new_window}.

### IBM Cloud Mass Data Migration
{: #mdms}

Un modo veloce, semplice e sicuro per trasferire fisicamente da terabyte a petabyte di dati in {{site.data.keyword.Bluemix_notm}}. Mass Data Migration è un dispositivo di archiviazione mobile con 120 TB di capacità di archiviazione utilizzabile per accelerare lo spostamento dei dati in {{site.data.keyword.Bluemix_notm}}. Supera le comuni sfide di trasferimento come ad esempio costi elevati, lunghi tempi di trasferimento e problemi di sicurezza, tutto in un unico servizio.

![Vista del dispositivo Mass Data Migration](images/mdms.svg)

Per ulteriori informazioni sul dispositivo Mass Data Migration, vedi: [Introduzione a IBM Cloud Mass Data Migration](/docs/infrastructure/mass-data-migration/index.html#getting-started-with-ibm-cloud-mass-data-migration){:new_window}.

