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

# Audit
{: #audit}

Methoden zur Durchführung von Audits für Aktivitäten in der {{site.data.keyword.Db2_on_Cloud_short}}-Datenbank sind im Folgenden aufgeführt:

* [Ereignismonitor CHANGE HISTORY![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

Sie können einen CHANGE HISTORY-Ereignismonitor erstellen, um die Ereignismonitortabelle abzufragen und so festzustellen, welche Aktionen in der Datenbank stattgefunden haben und wer sie ausgeführt hat. 

Die Time Travel Query-Funktion bietet eine einfache Möglichkeit, alle Änderungen an den Daten zu speichern und alte Daten auf der Basis eines ausgewählten Zeitpunkts abzufragen. Wenn Sie diese Auditmethode verwenden möchten, müssen Sie sicherstellen, dass zuerst die Tabellen so eingerichtet werden, dass sie Time Travel Query unterstützen.

Weitere Informationen zu diesen Auditmethoden finden Sie im Abschnitt [Wie können Änderungen verfolgt oder protokolliert werden? ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.
