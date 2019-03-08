---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

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

# Migration de données vers IBM Cloud
{: #migration}

Vous pouvez charger des données à partir d'un fichier de données dans un format délimité (par exemple, CSV ou TXT) situé sur un réseau local ou dans un magasin de données (Amazon S3 ou IBM Cloud Object Storage) vers {{site.data.keyword.Db2_on_Cloud_long}}. Vous pouvez même migrer vos données à partir d'un système sur site.
{: shortdesc}

## Chargement de données depuis un conteneur d'objets
{: #cos}

Pour charger des données depuis Amazon S3, sélectionnez l'une des méthodes suivantes :
  * Depuis la console Web {{site.data.keyword.Db2_on_Cloud_short}} : **Charger > Amazon S3**. 
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

Pour charger les données depuis IBM Cloud Object Storage en utilisant directement des tables externes, prenez connaissance de l'instruction SQL exemple suivante :

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )      
```

Pour IBM Cloud Object Storage, pour créer des données d'identification HMAC lors de la création de nouvelles données d'identification de service, spécifiez {"HMAC:true"} dans la zone *Ajouter des paramètres de configuration en ligne*.
{: note}

## Migration de données depuis un système sur site
{: #onprem}

Pour migrer vos données à partir d'un système sur site, choisissez l'une des méthodes suivantes selon la taille de votre jeu de données :
* Moins de 25 To de données : [Interface de ligne de commande IBM Lift](#lift)
* 25 To de données et plus : [IBM Cloud Mass Data Migration](#mdms)

### Interface de ligne de commande IBM Lift
{: #lift}

L'interface de ligne de commande Lift est une application gratuite que vous pouvez utiliser pour migrer vos données dans {{site.data.keyword.Bluemix_notm}} à partir des différentes sources de données répertoriées dans le tableau 1. 

| Base de données cible dans IBM Cloud | Source de données |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle Database |
|                              | Microsoft SQL Server |
|                              | Format de fichier CSV |
{: caption="Tableau 1. Migration de sources de données" caption-side="top"}

Pour télécharger et installer l'interface de ligne de commande Lift, voir [Download Lift CLI ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#download){:new_window}.

Pour des instructions pas à pas relatives à la migration de vos données dans {{site.data.keyword.Bluemix_notm}} en utilisant Lift, voir : [Migrate data to {{site.data.keyword.Db2_on_Cloud_long_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://lift.ng.bluemix.net/#docs){:new_window}.

### IBM Cloud Mass Data Migration
{: #mdms}

Il s'agit d'une méthode rapide, simple et sécurisée pour le transfert physique de téraoctets ou de pétaoctets de données vers {{site.data.keyword.Bluemix_notm}}. MDMS (Mass Data Migration) est un périphérique de stockage mobile proposant 120 To de capacité de stockage utilisable pour accélérer le déplacement des données vers {{site.data.keyword.Bluemix_notm}}. Il vous permet de relever les défis posés quotidiennement par le transfert de gros volumes d'informations : coûts élevés, temps de transfert longs et problèmes de sécurité – tout ceci, dans un seul et même service.

![Vue du périphérique Mass Data Migration](images/mdms.svg)

Pour plus d'informations sur le périphérique Mass Data Migration, voir [Getting started with IBM Cloud Mass Data Migration](/docs/infrastructure/mass-data-migration/index.html#getting-started-with-ibm-cloud-mass-data-migration){:new_window}.

