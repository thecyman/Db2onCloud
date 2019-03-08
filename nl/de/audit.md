---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# Audits, Protokollierung und Überwachung
{: #aud-log-mon}

## Audit durchführen
{: #auditing}

Sie können eine Auditrichtlinie für die Datenbank erstellen, die es Ihnen ermöglicht, Audits für verschiedene Ereigniskategorien durchzuführen, die in Auditereignistabellen in Ihrer Datenbank gespeichert sind. Weitere Informationen finden Sie in [Anleitungen für Auditrichtlinien ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}.

Darüber hinaus können Sie die folgenden Methoden für das Durchführen von Audits und die Verfolgung von Datenbankänderungen verwenden:
* Sie können einen `CHANGE HISTORY`-Ereignismonitor erstellen, um die Ereignismonitortabelle abzufragen und so festzustellen, welche Aktionen in der Datenbank stattgefunden haben und wer sie ausgeführt hat. Weitere Informationen finden Sie in [Ereignismonitor `CHANGE HISTORY` ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}.
* Die Time Travel Query-Funktion bietet eine einfache Möglichkeit, alle Änderungen an den Daten zu speichern und alte Daten auf der Basis eines ausgewählten Zeitpunkts abzufragen. Wenn Sie diese Auditmethode verwenden möchten, müssen Sie sicherstellen, dass zuerst die Tabellen so eingerichtet werden, dass sie Time Travel Query unterstützen. Weitere Informationen finden Sie in [Time Travel Query ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}.

Weitere Informationen zur Durchführung von Audits und zur Verfolgung von Datenbankänderungen finden Sie in [Wie werden Audits durchgeführt und Änderungen verfolgt? ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Protokollierung und Überwachung
{: #log_mon}

Überwachung und Protokollierung sind Teil des Service, diese Funktionen sind jedoch nicht direkt für den Benutzer zugänglich. Stattdessen wird die Infrastruktur von den Mitarbeitern des operativen IBM Teams verwendet, um Probleme zu beheben.  

Informationen zur Verfügbarkeit von Activity Tracker finden Sie in [Roadmap ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/db2oncloud-roadmap){:new_window}.

Sie können eine Verbindung über einen Db2-Befehlszeilenclient wie z. B. CLPPlus herstellen, um auf detaillierte Informationen und Diagnosen zuzugreifen.

### Basisübersicht:
{: #basic_overview}

Es sind zwei Basistypen der Überprüfung verfügbar. Hierbei handelt es sich um externe Status- und Verfügbarkeitsüberprüfungen sowie die metrikgestützte Überwachung. IBM überwacht mehrere Hundert Metriken und speichert diese Metriken als Langzeitdaten. Auf der Basis der Werte dieser Metriken werden Alerts generiert. Diese Alerts werden an die Mitarbeiter des operativen IBM Teams gesendet, um sicherzustellen, dass die Alerts bearbeitet werden. Darüber hinaus sendet IBM auch archivierte Betriebssystem- und Diagnoseprotokolle, mit denen eine schnelle Diagnose möglich ist. {{site.data.keyword.Db2_on_Cloud_short}} erfüllt die Vorgaben der DSGVO. Bei Bedarf kann mit den IBM EU Cloud-Optionen eine noch striktere Einhaltung der DSGVO-Vorgaben umgesetzt werden.


