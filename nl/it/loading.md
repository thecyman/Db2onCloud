---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-23"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Caricamento dei dati 
{: #load}

Puoi caricare i dati da un file di dati in un formato delimitato come CSV o TXT ubicato su una rete locale, un archivio oggetti (Amazon S3 o IBM Cloud Object Storage (in precedenza SoftLayer Swift)) o utilizzando gli strumenti Db2®. Puoi anche compilare un'istanza del database con i dati eseguendo un processo di caricamento da un'applicazione come InfoSphere® DataStage®.
{: shortdesc}

* [Caricamento dei dati con Lift CLI ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Caricamento dei dati da Oracle ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Caricamento dei dati da SQL Server ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Caricamento dei dati un file CSV ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* Carica i dati da Amazon S3 utilizzando uno dei seguenti metodi: 
    * Console web {{site.data.keyword.dashdbshort_notm}}. **Load > Amazon S3**. 
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
<!-- * [Loading data from Amazon S3 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/s3.html){:new_window} -->
