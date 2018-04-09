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

# Daten laden
{: #load}

Sie können Daten aus einer Datendatei laden, die in einem Format mit Begrenzern, z. B. CSV oder TXT, vorliegt und sich in einem lokalen Netz befindet; oder Sie können Daten aus einem Objektspeicher (Amazon S3 oder IBM Cloud Object Storage (früher als SoftLayer Swift bezeichnet)) oder mithilfe von Db2®-Tools laden. Darüber hinaus können Sie eine Datenbankinstanz mit Daten füllen, indem Sie einen Ladeprozess über eine Anwendung wie InfoSphere® DataStage® ausführen.
{: shortdesc}

* [Daten mit der Lift-Befehlszeilenschnittstelle laden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Daten aus Oracle laden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Daten aus SQL Server laden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#docs){:new_window}
* [CSV-Datei laden ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/#docs){:new_window}
<!-- * [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->
* Sie können Daten von Amazon S3 mithilfe einer der folgenden Methoden laden:
    * Über die {{site.data.keyword.dashdbshort_notm}}-Webkonsole. **Laden > Amazon S3**. 
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
<!-- * [Loading data from Amazon S3 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/s3.html){:new_window} -->
