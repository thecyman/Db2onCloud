---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Sicherung und Wiederherstellung
{: #bnr}

Bei kostenpflichtigen Plänen werden täglich verschlüsselte Sicherungen der Datenbank durchgeführt. Eine tägliche Sicherung wird für jeden der letzten 14 Tage aufbewahrt.
{: shortdesc}

Zusätzlich zu Standardsicherungen können Sie mithilfe der [Time Travel Query ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} Langzeitdaten für andere Zwecke speichern, z. B. für schnelle Abfragen alter Daten oder für die vereinfachte Durchführung von Audits. Darüber hinaus können Sie mithilfe von IBM Data Studio oder einem beliebigen Db2-Tool eigene Exporte durchführen.
 
Informationen zur zeitpunktgesteuerten Wiederherstellungen finden Sie in [Zeitpunktgesteuerte Wiederherstellung](#point-in-time).

In allen kostenpflichtigen Plänen wird normalerweise IBM Cloud Object Storage (COS) verwendet, um Sicherungen an 3 verschiedene Rechenzentren auszulagern. Sydney und bestimmte kleinere Rechenzentren unterstützten jedoch zum gegenwärtigen Zeitpunkt möglicherweise keine ausgelagerte Replikation mit IBM COS. In der [Dokumentation zu IBM COS](/docs/services/cloud-object-storage/basics/endpoints.html#select-regions-and-endpoints) für die jeweilige Region finden Sie Informationen dazu, welche Regionen die ausgelagerte Replikation unterstützen.

<!-- Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool. -->

<!-- To store your backups offsite at a remote storage site, make a request to IBM Support. -->

Sie können auch die [IBM Lift-Befehlszeilenschnittstelle ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lift.ng.bluemix.net/){:new_window} verwenden, um Daten in {{site.data.keyword.Db2_on_Cloud_short}} zu importieren.

## Zeitpunktgesteuerte Wiederherstellung
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} ist nun eine Funktion zur zeitpunktgesteuerten Wiederherstellung verfügbar. Diese ermöglicht die Wiederherstellung der gesicherten Daten für einen exakten Zeitpunkt. Derzeit müssen die meisten Kunden Unterstützung zur Aktivierung dieses Features anfordern. Weitere Informationen dazu enthält der folgende Rollout-Plan.

Eine Verfügbarkeitsliste des Features für die zeitpunktgesteuerte Wiederherstellung ist nachfolgende aufgeführt:
- Rechenzentrum Dallas: Derzeit verfügbar auf Einzelserversystemen.
- Alle anderen, einschließlich Europa und HA-Systeme in Dallas: Aktivierung des Features muss beim Support angefordert werden. Der vollständige Rollout für alle Systeme wird bis 28. Februar 2019 abgeschlossen sein.
- IBM Cloud Dedicated-System (früher Bluemix Dedicated): Verfügbarkeit nur durch das Öffnen eines Support-Tickets.

Mit den folgenden ausgewählten Beispielen für Screenshots der Webkonsolenbenutzerschnittstelle wird veranschaulicht, wie die zeitpunktgesteuerte Wiederherstellungsoperation initiiert und der Fortschritt angezeigt wird:

1. Wählen Sie die Wiederherstellungsstrategie **Zeitpunktgesteuert** und anschließend das gewünschte Datum für die zeitpunktgesteuerte Wiederherstellung der Datenbank aus. Der zeitpunktgesteuerte Wiederherstellungsprozess wählt die Sicherung, die dem gewünschten Datum am nächsten liegt, aus dem Pool der gespeicherten Sicherungen aus, die während der vorherigen 14 Tage erstellt wurden. 

   Der zeitpunktgesteuerte Wiederherstellungsprozess legt alle zuvor gespeicherten Sicherungen, deren Datum nach dem für die zeitpunktgesteuerte Wiederherstellung ausgewählten Datum liegt, als ungültig fest, da sich eine Abweichung in der Zeitachse ergibt.
   {: note}

   ![Ansicht der hervorgehobenen Auswahl für die zeitpunktgesteuerte Wiederherstellungsstrategie](images/pit_restore_1.png)

2. Bestätigen Sie, dass Sie den Vorgang mit den ausgewählten Wiederherstellungsptionen fortsetzen möchten. Nach dem Initiieren der Wiederherstellungsoperation können Sie die Anforderung nicht mehr ändern.  
![Ansicht des Bestätigungsdialogs für die zeitpunktgesteuerte Wiederherstellung](images/pit_restore_2.png)

3. Der Wiederherstellungsprozess wird initialisiert.
![Ansicht der Initialisierung der zeitpunktgesteuerten Wiederherstellung](images/pit_restore_3.png)

4. Die Datenbank wird am ausgewählten Zeitpunkt wiederhergestellt.
![Ansicht des Fortschritts der zeitpunktgesteuerten Wiederherstellung](images/pit_restore_4.png)

5. Es wird ein neuer Sicherungspunkt erstellt. Die zeitpunktgesteuert wiederhergestellte Datenbank ist zur Verwendung bereit.
![Ansicht der Erstellung des neuen Sicherungspunkts](images/pit_restore_5.png)

6. Die Wiederherstellungsoperation wurde erfolgreich abgeschlossen.
![Ansicht des erfolgreichen Abschlusses der Wiederherstellungsoperation](images/pit_restore_6.png)

