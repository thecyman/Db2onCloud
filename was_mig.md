---

copyright:
  years: 2014, 2019
lastupdated: "2018-08-23"

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

# Migrating WebSphere Application Server database to IBM Cloud
{: #mig_was}



{{site.data.keyword.Db2_on_Cloud_long}}
{{site.data.keyword.Db2_on_Cloud_short}}
{: shortdesc}



## WAS DB



## Application DB





**Notes**

You can migrate WebSphere to the cloud and run it there. Lots of documentation about this.

Use this tool to "clone" your Websphere implementation in the cloud and run v9 there:
[WebSphere Configuration Migration Tool for IBM Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/wasdev/downloads/#asset/tools-WebSphere_Configuration_Migration_Tool_for_IBM_Cloud){:new_window}.

At this point, I see no docs that describe how to migrate WebSphere backend database to the cloud. Dalia provided link to doc that describes making a secure connection between WebSphere running in the cloud and its database located on premises by using a secure gateway.

This topic could discuss migrating WebSphere and its database to the cloud. Any app-based database can be migrated traditionally with Lift. If WAS DB is small to store its cfgs, then it's not likely users will want to separate it from WAS installation location and risk perf hit. If a DB is created to store transactional data for an app, then that's the DB that is connected to thru WAS with its JCA spec connector facility. The DB is used by the app to retrieve and persist data.
[WebSphere Application Server: Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SSAW57_9.0.0/com.ibm.websphere.nd.multiplatform.doc/ae/welc6productov.html){:new_window}

Data from DBs can be migrated to a transactional DB in the cloud to store and retrieve tranasactional data, or to a warehouse DB to eventually be analyzed.