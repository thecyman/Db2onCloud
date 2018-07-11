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

The standard high availability plans without a DR node provide seamless failover and rolling updates. They are managed for you by using automatic client reroute (ACR) and portable IPs.

In addition, you can add a Geo-Replicated Disaster Recovery Node. This offsite DR node option gives you the ability to rapidly synchronize your data in real time to a database node in an offsite {{site.data.keyword.Bluemix_notm}} data center of your choice. 

[List of data center locations where DR nodes are available. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} uses the Db2 High Availability Disaster Recovery (HADR) technology in `ASYNC` mode to achieve the offsite DR node capability and provides `Read on Standby` on the DR node.

# How to add a Geo-Replicated Disaster Recovery Node
{: #add_dr}
For existing Db2 on Cloud users:
 * You can add an DR node on-demand to existing {{site.data.keyword.Db2_on_Cloud_short}} instances. After clicking your instance in the {{site.data.keyword.Bluemix_notm}} dashboard, you will see an option called "Manage Disaster Recovery". You can add a Geo-Replicated Disaster Recovery Node from there.
 * If you purchased Db2 on Cloud on contract via a sales representative and do not have an IBM Cloud subscription, please contact your IBM representative to add a DR Node.
If you are currently not a Db2 on Cloud user:
 * Order Db2 on Cloud via IBM Cloud, or speak to your sales representative.
 * You can then add a DR node using the steps above. (Using the "Manage Disaster Recovery" in the console.)
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

# Managing High Availability and Disaster Recovery Nodes
For standard HA nodes (which are not offsite), the failover is managed for you by IBM. IBM will monitor the health of your server and fail over and back as needed, including for rolling updates and scaling to keep uptime as high as possible.

For Geo-Replicated Disaster Recovery (HADR), you will need to manually fail over using the "Manage Disaster Recovery" console. In addition, [you can fail over using APIs described here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}.
