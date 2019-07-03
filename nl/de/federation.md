---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-26"

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

# Datenvirtualisierung (Föderierung)
{: #fed}

Die Db2-Datenvirtualisierung (auch als Föderierung bezeichnet) wird von {{site.data.keyword.Db2_on_Cloud_short}} unterstützt. Mithilfe der Datenvirtualisierung können Sie über eine einzelne Abfrage auf alle Daten zugreifen, die sich auf mehreren verteilten Datenbanken innerhalb Ihres Unternehmens befinden. Sie können auf Daten zugreifen, die in beliebigen Ihrer Db2- oder Informix-Datenquellen sowohl lokal als auch in der Cloud gespeichert sind. 
{: shortdesc}

Diese Funktion wird in allen Versionen von {{site.data.keyword.Db2_on_Cloud_short}} unterstützt, allerdings nicht im Rahmen des kostenfreien Lite-Plans. Der Lite-Plan kann jedoch als Ziel verwendet werden, aus dem Daten abgerufen werden.

## Anwendungsfälle
{: #use_cases}

### Datenquellen konsolidieren

Indem Sie die Datenquellen, die sich sowohl in der Cloud als auch lokal an einer beliebigen Speicherposition innerhalb Ihrer Organisation befinden, föderieren, können Sie virtualisierte Daten so abrufen, als ob sie aus einer einzelnen Quelle stammen. Durch die Datenvirtualisierung entfällt der umständliche und kostenintensive Datenmigrationsprozess und Sie erhalten die Möglichkeit, alle Ihre Daten effizient und kostenwirksam zu analysieren.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Mit Db2 Warehouse on Cloud verbinden

Benutzer von Produkten der Db2-Produktfamilie können Daten aus {{site.data.keyword.Db2_on_Cloud_short}}- und {{site.data.keyword.dashdbshort_notm}}-Datenbanken föderieren. Über eine einheitliche Schnittstelle für den Datenzugriff können Sie ohne großen Aufwand Daten hinzufügen, abfragen und analysieren, ohne dass komplexe ETL-Prozesse oder zusätzlicher Code erforderlich sind.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### Auf mehrere Server aufgeteilte Daten

In bestimmten Situationen kann es sinnvoll sein, Daten zu partitionieren (aufzuteilen). Die Föderierungsfunktionen ermöglichen das Abfragen von aufgeteilten Daten über eine einheitliche Schnittstelle. Mithilfe der Föderierung können Sie Workloads besser ausgleichen, bestimmte Teile einer App skalieren und Mikroservices erstellen, die interagieren. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### Datenbankkapazität über festgelegte Grenzwerte hinaus erhöhen

Die Föderierungsfunktionen ermöglichen es Ihnen, die Kapazität einer lokalen Datenbank zu erhöhen, indem Sie sie mit einer Datenbank in der Cloud föderieren. Die Datenvirtualisierung bietet in diesem Fall eine nützliche Option, falls der Speicherplatz der lokalen Datenbank knapp wird. Das Erhöhen der Kapazität einer Datenbank mithilfe der Föderierung ist besonders für die Neuentwicklung geeignet, da die Entwickler eine bereits in Produktion befindliche Datenbank nicht mehr ändern müssen. Auch die Föderierung zwischen zwei {{site.data.keyword.Db2_on_Cloud_short}}-Datenbanken ist möglich, um die Datenbankkapazität über die aktuellen Grenzwerte des Flex-Plans hinaus zu erhöhen.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## Einführung
{: #getting_started_fed}

In den folgenden Schritten wird anhand eines Beispiels veranschaulicht, wie unterschiedliche, verteilte Datenquellen föderiert werden können, damit Daten so abgerufen werden können, als ob sie aus einer einzelnen Quelle stammen. Das folgende Beispiel stellt die Föderierung zweier {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank dar:

### Auf der Db2 on Cloud-Zielmaschine
{: #targ}

Hostname: targetdotcom

1. Erstellen Sie eine Tabelle mit der Bezeichnung `testdata` im Schema `admin2`.

2. Laden Sie in der {{site.data.keyword.Db2_on_Cloud_short}}-Konsole die Tabelle `testdata` mit den Daten als Benutzer `admin2` mit dem Kennwort `YYYY`.

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

### Auf einer Db2 on Cloud-Maschine, die als Föderierungsquelle verwendet wird
{: #fed_src}

Führen Sie in der {{site.data.keyword.Db2_on_Cloud_short}}-Konsole die folgenden Schritte aus:

1. Erstellen Sie einen Server für die Kommunikation mit der Zielmaschine:<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   Beispiel: <br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. Erstellen Sie eine Benutzerzuordnung für admin2:<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   Beispiel:<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. Erstellen Sie einen Kurznamen für die Datenbank: <br/>
   `create nickname <nickname> for <server_name>.<schema_name>.<table_name>`

   Beispiel:<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. Testen Sie, ob Daten vom Zielserver abgerufen werden können:<br/>
   `select * from <nickname>`

   Beispiel:<br/>
   `select * from ntest1`

## Zusätzliche Informationen
{: #more_info}

Weitere Informationen zur Datenvirtualisierung (Föderierung) finden Sie in [Föderierung![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}.

Standardmäßig unterstützt {{site.data.keyword.Db2_on_Cloud_short}} Informix und Db2 (einschließlich der lokalen Version von Db2 und Db2 Warehouse). Die Unterstützung für bestimmte Datenquellen muss möglicherweise von IBM Support auf Anforderung installiert werden. Informationen zu den Datenquellen, die durch die Föderierung unterstützt werden, finden Sie in [Durch die Föderierung unterstützte Datenquellen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}.

