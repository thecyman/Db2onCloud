---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# Free plan
{: #free_plan}

The {{site.data.keyword.Db2_on_Cloud_long}} Free plan provides basic resources to let you develop or learn about Db2 without charge.
{: shortdesc}

There is no time limit on the Free plan, but users must re-extend their Free plan every 30 days.

Only community support is available. 
 
## Architecture
{: #architecture}

Unlike other {{site.data.keyword.Db2_on_Cloud_short}} plans, the {{site.data.keyword.Db2_on_Cloud_short}} Free plan runs on a multi-tenant system. The Flex and Precise Performance plans run on their own single-tenant virtual machines or baremetal servers.
 
The Free plan allows you to use one database schema.

For more information about the {{site.data.keyword.Db2_on_Cloud_short}} Free plan, see the [FAQ ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oc_free_plan_faq){:new_window}.

## Using the Free plan outside continental North America
{: #outside_na}

The Free plan is currently accessible without a credit card for continental North America. Outside of continental North America, customers must add a credit card to their IBM Cloud account and then select the "US South - Dallas" region for the Free plan to be visible for selection.

The Free plan is always free and your credit card will not be charged.

## Free plan restrictions
{: #fp_restrictions}

You are strongly recommended to use an enterprise-level service plan rather than a Free service plan for mission-critical or performance-sensitive workloads. 
{: important}

The following is a table of {{site.data.keyword.Db2_on_Cloud_short}} Free plan restrictions:

| Category | Item | Restriction | 
|----------|------|-------------|
| Resources | Storage | 200 MB of storage per user |
|  | Connections | 5 connections per user |
|  | Performance | Performance might fluctuate due to workloads run by other users on the multi-tenant system |
|  |  |
| Features & functions | Federation | Not supported |
|  | Oracle compatibility | Not supported |
|  | User-defined extensions (UDFs) | Not supported on any {{site.data.keyword.Db2_on_Cloud_short}} plans, including the Free plan |
|  | User management | User not given administrative authority |
|  | Row and column access control (RCAC) | Not supported |
|  | IBM InfoSphere Data Replication for use in loading data | Not supported |
|  |  |
| Networking environment | IBM Cloud Integrated Analytics | Not supported |
|  | IBM Cloud Dedicated | Not supported |
|  |  |
| Security compliances | Health Information Portability and Accountability Act of 1996 (HIPAA) | Not supported. Refer to your Service Description. |
|  | EU General Data Protection Regulation (GDPR) | Not supported. Refer to your Service Description. |
|  |  |
| Account management | Reactivation | Reactivation required every 30 days. If not reactivated, Free plan services are deleted 60 days later.  |
{: caption="Table 1. {{site.data.keyword.Db2_on_Cloud_short}} Free plan restrictions" caption-side="top"}


