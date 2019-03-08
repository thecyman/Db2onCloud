---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-22"

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

# Hochverfügbarkeit (High Availability, HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}}-Hochverfügbarkeitspläne weisen mit einem SLA von 99,99 % ausgezeichnete Verfügbarkeitsmerkmale auf. 
{: shortdesc}

Die Standardhochverfügbarkeitspläne ohne DR-Knoten (Disaster Recovery) bieten eine nahtlose Funktionsübernahme und rollierende Aktualisierungen. Sie werden mithilfe von automatischer Clientweiterleitung (ACR) und portierbaren IPs verwaltet.

Darüber hinaus kann ein DR-Knoten (Disaster Recovery) mit Georeplikation hinzugefügt werden. Diese Option eines ausgelagerten DR-Knotens ermöglicht die schnelle Echtzeitsynchronisierung von Daten auf einen Datenbankknoten an einem von Ihnen ausgewählten ausgelagerten {{site.data.keyword.Bluemix_notm}}-Rechenzentrum. 

[Liste der Standorte von Rechenzentren mit verfügbaren DR-Knoten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} verwendet die Db2 HADR-Technologie (High Availability Disaster Recovery) im asynchronen Modus (`ASYNC`), um die Funktion des ausgelagerten Disaster-Recovery-Knotens bereitzustellen, und ermöglicht Leseoperationen in der Bereitschaftsdatenbank (`Read on Standby`) auf dem DR-Knoten.

## **Brasilien: Ergänzende Regel 14** (gültig für Systeme, die für die brasilianische Regierung eingerichtet werden)
{: #rule_14}

Zum gegenwärtigen Zeitpunkt ist die DR-Option (Disaster Recovery) für Db2 on Cloud-Angebote aufgrund der ergänzenden Regel 14 für Systeme, die für die brasilianische Regierung eingerichtet werden, nicht verfügbar.

## Vorgehensweise für das Hinzufügen eines DR-Knotens mit Georeplikation
{: #add_dr}

Für vorhandene {{site.data.keyword.Db2_on_Cloud_short}}-Benutzer:
 * Sie können einen bedarfsgesteuerten DR-Knoten zu vorhandenen {{site.data.keyword.Db2_on_Cloud_short}}-Instanzen hinzufügen. Nach dem Klicken auf die Instanz im {{site.data.keyword.Bluemix_notm}}-Dashboard wird die Option **Disaster Recovery verwalten** angezeigt. Hier können Sie einen DR-Knoten mit Georeplikation hinzufügen.
 * Wenn Sie {{site.data.keyword.Db2_on_Cloud_short}} durch das Abschließen eines Vertrags mit einem Vertriebsbeauftragten erworben haben und nicht über ein {{site.data.keyword.Bluemix_notm}}-Abonnement verfügen, wenden Sie sich für das Hinzufügen eines DR-Knotens an den zuständige IBM Ansprechpartner.

Wenn Sie zurzeit kein {{site.data.keyword.Db2_on_Cloud_short}}-Benutzer sind:
 * Bestellen Sie {{site.data.keyword.Db2_on_Cloud_short}} über {{site.data.keyword.Bluemix_notm}} oder wenden Sie sich an den zuständigen Vertriebsbeauftragten.
 * Sie können dann einen DR-Knoten hinzufügen, indem Sie die Option **Disaster Recovery verwalten** in der Konsole verwenden.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## HADR-Knoten (High Availability Disaster Recovery) verwalten
{: #manage_ha_dr}

Bei Standardhochverfügbarkeitsknoten, die nicht ausgelagert sind, wird die Funktionsübernahme von IBM verwaltet. IBM überwacht den Serverstatus und führt Failover- und Failbackoperationen nach Bedarf aus, einschließlich rollierender Aktualisierungen und Skalierung, um eine möglichst hohe Verfügbarkeitszeit zu erreichen.

Bei der Disaster Recovery mit Georeplikation (HADR) müssen Sie die Funktionsübernahme manuell durchführen, indem Sie die Option **Disaster Recovery verwalten** in der Konsole verwenden. Darüber hinaus können Sie die Funktionsübernahme auch mithilfe einer API durchführen. Eine Beschreibung finden Sie [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}.

## Häufig gestellte Fragen
{: #faq}

### Welche Änderungen sind für eine Anwendung, die Db2 verwendet, erforderlich, um die Arbeit mit dem DR-Knoten nach der Übernahme zu ermöglichen? Wird der DNS-Name oder die IP-Adresse nach der Übernahme geändert?

**A**: Nein. Sie erhalten zwei auflösbare Hostnamen. Wenn die App so konfiguriert ist, dass sie Db2 ACR (Active Connection Reroute) verwendet, wird sie an den neuen Primärknoten weitergeleitet.

Weitere Informationen zum DR-Knoten mit Georeplikation können Sie aufrufen, indem Sie [hier ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window} klicken.
