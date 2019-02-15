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

# Daten in IBM Cloud migrieren
{: #migration}

Sie können Daten aus einer Datendatei im Format mit Begrenzern (CSV oder TXT), die sich in einem lokalen Netz oder in einem Objektspeicher (Amazon S3 oder IBM Cloud Object Storage) befindet, in {{site.data.keyword.Db2_on_Cloud_long}} laden. Es ist auch möglich, Daten von einem lokalen System zu migrieren.
{: shortdesc}

## Daten aus dem Objektspeicher laden
{: #cos}

Wählen Sie eine der folgenden Methoden aus, um Daten aus Amazon S3 zu laden:
  * Über die {{site.data.keyword.Db2_on_Cloud_short}}-Webkonsole. **Laden > Amazon S3**. 
  * Direkt über die externen Tabellen. Im Folgenden ist eine SQL-Beispielanweisung dargestellt:

    ```
    INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
        (CCSID 1208 s3('s3.amazonaws.com', 
        '<S3-access-key-ID>',
        '<S3-secret-access-key>', 
        '<my_bucket>'
           )
      )      
    ```

Im Folgenden ist eine SQL-Beispielanweisung dargestellt, mit der Daten direkt mithilfe externer Tabellen aus IBM Cloud Object Storage geladen werden:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )      
```

Geben Sie für IBM Cloud Object Storage {"HMAC:true"} im Feld *Inline-Konfigurationsparameter hinzufügen* an, um beim Erstellen neuer Serviceberechtigungsnachweise HMAC-Berechtigungsnachweise zu erstellen.
{: note}

## Daten aus einem lokalen System migrieren
{: #onprem}

Wählen Sie abhängig von der Größe des verwendeten Datasets eine der folgenden Methoden aus, um Daten aus einem lokalen System zu migrieren:
* Weniger als 25 TB an Daten: [IBM Lift-Befehlszeilenschnittstelle](#lift)
* 25 TB und mehr an Daten: [IBM Cloud Mass Data Migration](#mdms)

### Lift-Befehlszeilenschnittstelle
{: #lift}

Bei der Lift-Befehlszeilenschnittstelle handelt es sich um eine Anwendung, die Sie kostenfrei nutzen können, um Ihre Daten aus den verschiedenen, in Tabelle 1 aufgeführten Datenquellen in {{site.data.keyword.Bluemix_notm}} zu migrieren. 

| Zieldatenbank in IBM Cloud | Datenquelle |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Oracle-Datenbank |
|                              | Microsoft SQL Server |
|                              | CSV-Dateiformat |
{: caption="Tabelle 1. Migrationsdatenquellen" caption-side="top"}

Informationen zum Download und zur Installation der Lift-Befehlszeilenschnittstelle finden Sie in [Lift-Befehlszeilenschnittstelle herunterladen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#download){:new_window}.

Eine in einzelne Schritte unterteilte Anleitung zur Migration Ihrer Daten in {{site.data.keyword.Bluemix_notm}} mithilfe der Lift-Befehlszeilenschnittstelle finden Sie in [Daten in {{site.data.keyword.Db2_on_Cloud_long_notm}} migrieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#docs){:new_window}.

### IBM Cloud Mass Data Migration
{: #mdms}

Hierbei handelt es sich um eine schnelle, einfache und sichere Möglichkeit, Datenvolumen von mehreren Tera- oder Petabyte physisch in {{site.data.keyword.Bluemix_notm}} zu transferieren. Mit Mass Data Migration steht ein mobiles Speichermedium mit 120 TB verwendbarer Speicherkapazität bereit, das das Verschieben von Daten in {{site.data.keyword.Bluemix_notm}} beschleunigen kann. Die gängigen Probleme bei der Datenübertragung, wie z. B. hohe Kosten, lange Übertragungsdauer und Sicherheitsaspekte, können überwunden werden - mit einem einigen Service.

![Ansicht des Mass Data Migration-Geräts](images/mdms.svg)

Weitere Informationen zum Mass Data Migration-Gerät finden Sie in [Einführung in IBM Cloud Mass Data Migration](/docs/infrastructure/mass-data-migration/index.html#getting-started-with-ibm-cloud-mass-data-migration){:new_window}.

