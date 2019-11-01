---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

keywords: 

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Maintenance and notification policies
{: #maint_note_pol}

The maintenance and notification policies for the {{site.data.keyword.Db2_on_Cloud_long}} service can be found in the [{{site.data.keyword.Bluemix_notm}} service descriptions](http://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){:external}. Additional terms of service specifically for {{site.data.keyword.Db2_on_Cloud_short}} can be found by looking under the **Chargeable additional SDs** category. 

Being acquainted with our policies can better help you plan and schedule your workloads to be resilient to system maintenance.
{: shortdesc}

## Maintenance policy
{: #maintenance}

When scheduled system maintenance must be done for the {{site.data.keyword.Db2_on_Cloud_short}} service, the major data centers (London, Dallas, and Sydney) are updated on separate days of the business week. **This gives customers the option to fail over to a DR node in a nearby data center to avoid maintenance, and fail back once maintenance completes.** All of the other data centers are simultaneously updated on a day of the week that doesn't coincide with the major data centers. Table 1 shows an example of a {{site.data.keyword.Db2_on_Cloud_short}} system maintenance schedule.

| Data center | Example of a possible maintenance schedule |
|-------------|-----------------------------|
| London | Monday |
| Dallas | Tuesday |
| Sydney | Wednesday |
| All others | Thursday |
{: caption="Table 1. Example of a system maintenance schedule" caption-side="top"}

The table is not an official system maintenance schedule, but an example of a possible maintenance schedule that demonstrates how maintenance might be done on different days for an update.
{: note}

## Notification policy
{: #notification}

Effective as of March 27, 2018, notification is sent to you two business days in advance of any scheduled system maintenance that can impact your {{site.data.keyword.Db2_on_Cloud_short}} service. 

The {{site.data.keyword.Db2_on_Cloud_short}} notification policy excludes the case in which we must address, in a timely manner, any security vulnerability that we deem to be an emergency-grade, time-sensitive issue. In that case, at least 24 hours advance notice is given as stipulated in the {{site.data.keyword.Bluemix_notm}} service descriptions.
