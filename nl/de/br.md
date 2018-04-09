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

# Sicherung und Wiederherstellung
{: #br}

Bei kostenpflichtigen Plänen werden täglich verschlüsselte Sicherungen der Datenbank durchgeführt. Eine tägliche Sicherung wird für jeden der letzten 14 Tage aufbewahrt.
{: shortdesc}

IBM verwendet die aufbewahrten Sicherungen, um im Falle einer Katastrophe oder eines Systemausfalls eine Systemwiederherstellung durchzuführen. Mithilfe der Funktion [Time Travel Query ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} können Sie Langzeitdaten für eigene Zwecke speichern. Darüber hinaus können Sie auch eigene Exporte durchführen, indem Sie IBM Data Studio oder ein anderes Db2-Tool verwenden.

Wenn Sie die Sicherungen an einen externen Speicherstandort auslagern möchten, senden Sie eine entsprechende Anforderung an IBM Support.

Sie können auch die [IBM Lift-Befehlszeilenschnittstelle](https://lift.ng.bluemix.net/){:new_window} zum Importieren von Daten in {{site.data.keyword.Db2_on_Cloud_short}} verwenden.
