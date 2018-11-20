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

New: Db2 on Cloud has added point-in-time restore capabilities. These allow you to restore to an exact point-in-time from your backups. The roll out schedule and availability of this feature is as follows:

Dallas data center on single server: Available today
Frankfurt, London data center on single server (non-EU Cloud region): Nov 29, 2018
All other single server, baremetal and HA or HADR system (non-EU Cloud, non-Bluemix Dedicated): Dec 20, 2018
EU Cloud Region: Open support ticket, or Jan 30, 2018
IBM Cloud Dedicated (formerly "Bluemix Dedicated"): Open support ticket. Rollout only on request.

Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool.

To store your backups offsite at a remote storage site, make a request to IBM Support.

You can also use [IBM Lift CLI](https://lift.ng.bluemix.net/){:new_window} to import data into {{site.data.keyword.Db2_on_Cloud_short}}.
