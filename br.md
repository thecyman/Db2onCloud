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

# Backup and restore
{: #br}

For paid plans, encrypted backups of the database are done daily. A daily backup is kept for each of the last 14 days.
{: shortdesc}

Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool.

To store your backups offsite at a remote storage site, make a request to IBM Support.

You can also use [IBM Lift CLI](https://lift.ng.bluemix.net/){:new_window} to import data into {{site.data.keyword.Db2_on_Cloud_short}}.
