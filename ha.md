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

High availability with an offsite disaster recovery (DR) node will be generally available on July 13, 2018 (currently, it's in closed beta). The offsite DR node gives you the ability to rapidly synchronize your data in real time to a database node in an offsite {{site.data.keyword.Bluemix_notm}} data center of your choice. 

[List of data center locations where DR nodes are available. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} uses the Db2 High Availability Disaster Recovery (HADR) technology in `ASYNC` mode to achieve the offsite DR node capability and provides `Read on Standby` on the DR node. After General Availability, you'll be able to add an on-demand DR node to existing {{site.data.keyword.Db2_on_Cloud_short}} instances.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
