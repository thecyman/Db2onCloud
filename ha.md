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

# High availability (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} high availability plans have excellent availability characteristics with a 99.99% SLA. 
{: shortdesc}

The standard high availability plans <!-- without a DR node -->provide seamless failover and rolling updates. They are managed for you by using automatic client reroute (ACR) and portable IPs.

High availability with an offsite disaster recovery node will be generally available shortly, on July 13, 2018. (It is currently in closed beta.) The offsite DR node gives you the ability to rapidly synchronize your data in real time to a database node in an offsite IBM Cloud data center of your choice. 

[Click here for a list of locations where DR nodes are available.![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} uses the Db2 High Availability Disaster Recovery (HADR) technology in ASYNC mode to achieve the offsite DR node capability, and provides Read on Standy on the disaster recovery node. Upon General Availability, customers will be able to add a DR node on-demand to existing Db2 on Cloud instances.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
