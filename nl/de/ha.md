---

copyright:
  years: 2014, 2018
lastupdated: "2018-03-14"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Hochverfügbarkeit (High Availability, HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}}-Hochverfügbarkeitspläne weisen mit einem SLA von 99,99 % ausgezeichnete Verfügbarkeitsmerkmale auf.
{: shortdesc}

Die Standardhochverfügbarkeitspläne <!-- without a DR node -->bieten eine nahtlose Funktionsübernahme und rollierende Aktualisierungen. Sie werden mithilfe von automatischer Clientweiterleitung (ACR) und portierbaren IPs verwaltet.

Hochverfügbarkeit mit einem ausgelagerten Disaster-Recovery-Knoten befindet sich zurzeit in einer exklusiven Betaphase. Wenden Sie sich an den zuständigen IBM Ansprechpartner, um Informationen zur Teilnahme an der exklusiven Betaphase zu erhalten. Der ausgelagerte Disaster-Recovery-Knoten ermöglicht die schnelle Echtzeitsynchronisierung von Daten auf einen Datenbankknoten an einem von Ihnen ausgewählten ausgelagerten Standort.{{site.data.keyword.Db2_on_Cloud_short}} verwendet die Db2 HADR-Technologie (High Availability Disaster Recovery) im asynchronen Modus, um die Funktion des ausgelagerten Disaster-Recovery-Knotens bereitzustellen, und ermöglicht Leseoperationen in der Bereitschaftsdatenbank auf dem Disaster-Recovery-Knoten.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
