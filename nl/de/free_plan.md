---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# Kostenfreier Plan
{: #free_plan}

Mit dem kostenfreien Plan für {{site.data.keyword.Db2_on_Cloud_long}} stehen Basisressourcen zur Verfügung, die Sie kostenfrei nutzen können, um sich mit Db2 vertraut zu machen und Entwicklungsaufgaben durchzuführen.
{: shortdesc}

Für den kostenfreien Plan gilt kein Zeitlimit, die Benutzer müssen den kostenfreien Plan jedoch alle 30 Tage verlängern.

Es steht lediglich Community-Unterstützung zur Verfügung. 
 
## Architektur
{: #architecture}

Im Gegensatz zu anderen {{site.data.keyword.Db2_on_Cloud_short}}-Plänen wird der kostenfreie Plan von {{site.data.keyword.Db2_on_Cloud_short}} mit einem Multi-Tenant-System ausgeführt. Der Flex-Plan und der Precise Performance-Plan werden auf eigenen virtuellen Einzeltenantmaschinen oder Bare-Metal-Servern ausgeführt.
 
Der kostenfreie Plan ermöglicht die Verwendung eines einzelnen Datenbankschemas. 

Weitere Informationen zum kostenfreien {{site.data.keyword.Db2_on_Cloud_short}}-Plan finden Sie auf der Seite mit den [häufig gestellten Fragen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/db2oc_free_plan_faq){:new_window}. 

## Den kostenfreien Plan außerhalb des nordamerikanischen Festlands verwenden
{: #outside_na}

Der kostenfreie Plan ist zurzeit ohne Kreditkarte für das nordamerikanische Festland verfügbar. Außerhalb des nordamerikanischen Festlands müssen Kunden eine Kreditkarte zu ihrem IBM Cloud-Konto hinzufügen und dann die Region "USA (Süden) - Dallas" auswählen, damit der kostenfreie Plan ausgewählt werden kann.

Für den kostenfreien Plan fallen keine Gebühren an und die Kreditkarte wird nicht belastet.

## Einschränkungen des kostenfreien Plans
{: #fp_restrictions}

Für geschäftskritische oder leistungskritische Workloads wird die Verwendung eines auf das Unternehmen abgestimmten Serviceplans anstelle eines kostenfreien Serviceplans unbedingt empfohlen.
{: important}

In der folgenden Tabelle sind die Einschränkungen des kostenfreien {{site.data.keyword.Db2_on_Cloud_short}}-Plans aufgeführt: 

| Kategorie | Element | Einschränkung | 
|----------|------|-------------|
| Ressourcen | Speicher | 200 MB Speicher pro Benutzer |
|  | Verbindungen | 5 Verbindungen pro Benutzer |
|  | Leistung | Die Leistung kann aufgrund von Workloads, die von anderen Benutzern im Multi-Tenant-System ausgeführt werden, fluktuieren. |
|  |  |
| Features & Funktionen | Föderierung | Nicht unterstützt |
|  | Oracle-Kompatibilität | Nicht unterstützt |
|  | Benutzerdefinierte Erweiterungen (UDFs) | In keinem der {{site.data.keyword.Db2_on_Cloud_short}}-Pläne unterstützt, auch nicht im kostenfreien Plan |
|  | Benutzerverwaltung | Benutzer erhält keine Administratorberechtigung |
|  |Zugriffssteuerung für Zeilen und Spalten (RCAC) | Nicht unterstützt |
|  | IBM InfoSphere Data Replication zur Verwendung beim Laden von Daten | Nicht unterstützt |
|  |  |
| Netzumgebung | IBM Cloud Integrated Analytics | Nicht unterstützt |
|  | IBM Cloud Dedicated | Nicht unterstützt |
|  |  |
| Einhaltung von Sicherheitsbestimmungen | Health Information Portability and Accountability Act von 1996 (HIPAA) | Nicht unterstützt. Siehe Servicebeschreibung. |
|  | Datenschutz-Grundverordnung der EU (DSGVO) | Nicht unterstützt. Siehe Servicebeschreibung. |
|  |  |
| Kontoverwaltung | Reaktivierung | Reaktivierung alle 30 Tage erforderlich. Wird keine Reaktivierung vorgenommen, werden die Services des kostenfreien Plans 60 Tage später gelöscht. |
{: caption="Tabelle 1. Einschränkungen des {{site.data.keyword.Db2_on_Cloud_short}}-Einstiegsplans" caption-side="top"}


