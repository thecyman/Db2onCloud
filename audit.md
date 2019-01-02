---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

<!-- Rimas, please change page name to: Audit, Logs & Monitoring -->

# Auditing, logging, and monitoring

## Auditing
{: #audit}

The following are methods by which you can audit activity on the {{site.data.keyword.Db2_on_Cloud_short}} database:

* [CHANGE HISTORY event monitor ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

By creating a CHANGE HISTORY event monitor, you can query the event monitor table to determine what was done within the database and by whom. 

The Time Travel Query makes it easy to store all of the changes to your data and even query your old data based on a selected point in time. To use this audit method, ensure that you first set up your tables to support Time Travel Query.

For more information about these audit methods, see [How do I audit or track changes? ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Logging and monitoring
{: #log_mon}

Monitoring and logging is part of the service, however, it is not directly exposed to the end user. Instead the infrastructure is used by IBM operational staff to address issues.  

<!-- For availability of the Activity Monitor, see the roadmap.-->

You can connect with a Db2 command line client, such as CLPPlus, to access detailed information and diagnostics.

### A basic overview:
{: #overview}

There are 2 basic types of checking. External health/uptime checks and metric-based monitoring. IBM monitors hundreds of metrics and stores those metrics historically. Based on the values of these metrics, alerts are generated. These alerts are sent to IBM operations staff to ensure the alerts are seen and addressed. In addition, IBM also sends archived operating system and diagnostic logs for rapid diagnosis. {{site.data.keyword.Db2_on_Cloud_short}} complies with GDPR, and IBM EU Cloud options provide an even higher level of adherence to GDPR, if needed.
