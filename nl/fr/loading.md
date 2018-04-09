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

# Chargement des données
{: #load}

Vous pouvez charger des données à partir d'un fichier de données dans un format délimité tel que CSV ou TXT situé sur un réseau local, depuis un magasin de données (Amazon S3 ou IBM Cloud Object Storage (anciennement SoftLayer Swift) ou à l'aide d'outils Db2®. Vous pouvez également remplir une instance de base de données en procédant au chargement à partir d'une application comme InfoSphere® DataStage®.
{: shortdesc}

* [Chargement des données avec l'interface de ligne de commande Lift ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Chargement des données à partir d'Oracle ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Chargement des données à partir de SQL Server ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Chargement d'un fichier CSV ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* Chargez des données à partir d'Amazon S3 à l'aide de l'une des méthodes suivantes : 
    * Depuis la console Web {{site.data.keyword.dashdbshort_notm}} : **Charger > Amazon S3**. 
    * Directement depuis des tables externes. Voici un exemple d'instruction SQL : 

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
