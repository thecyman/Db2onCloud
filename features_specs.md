---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-05"

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

# Features & specs
{: #overview}

{{site.data.keyword.Db2_on_Cloud_long}} features and specifications are summarized here for your convenience.
{: shortdesc}

| Category | Feature | Supported? | Comments |
|----------|---------|------------|----------|
| General | Db2 AESE | Y | Db2 v11.1.3.3 |
|  | Read on Standby | Y | Offsite DR node only |
|  | Automatic rolling updates | Y | With HA plans |
|  | Data center location options | Y | [Locations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-locations){:new_window}. See also: Deployment & scaling durations. |
|  | BLU in-memory | Y | Default is row, specify `CREATE TABLE..AS COL` for BLU |
|  | Activity Tracker | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Root access provided | N | Use Db2 Hosted if root access is required |
|  |  |  |  |
| High availability & replication | Offsite DR | Y | - |
|  | High availability (2 nodes in 1 zone) | Y | 99.99% uptime SLA |
|  | Different zones in same data center | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | **Note**: Offsite HADR is available |
|  | Change Data Capture (CDC) | Y | - |
|  | Use as HADR from on premises | N | Use CDC. For information, see [How can I migrate or sync data from Db2 to Db2 on Cloud? ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Autonomous failover - HA | Y | - |
|  | Autonomous failover - Offsite DR | N | Use button or API |
|  | IP moves with failover | Y | Local HA only; not offsite HADR |
|  | RPO: High Availability | 0 s | HA is synchronous |
|  | RTO: High Availability | Typically 0-10 min | With retry code, will appear as slowness with Db2 ACR |
|  | RPO: Offsite node HADR | Typically < 15 s | Offsite DR is asynchronous |
|  | RTO: Offsite node HADR | < 3 min | Must initiate with console button or API |
|  |  |  |  |
| System configurations | Max RAM and cores | 1 TB RAM, 48 cores | Applies to Precise Performance XL plan |
|  | Max storage | 11 TB | Applies to Precise Performance XL plan. Disk for both data and logs. |
|  | Flex: base plan | 4 GB RAM, 1 core, 2 GB disk | - |
|  | Flex: Max RAM and cores | 128 GB RAM, 32 cores | Need higher specs? Use Precise Performance plan or contact IBM Support. |
|  | Flex: Max storage | 4 TB | Disk for both data and logs. Need higher specs? Use Precise Performance plan or contact IBM Support. |
|  |  |  |  |
| Maintenance policies & SLAs | High availability plans | 99.99% | - |
|  | Single server plans | 99.5% | - |
|  | Offsite DR node | 99.5% | Must use additional local HA to achieve 99.99% |
|  | Maintenance policy | Y | [Read details ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| Security compliances | HIPAA Ready | Y | All paid plans including Flex. Must request HIPAA mode from IBM Support. <!--For Db2 Warehouse on Cloud [see docs here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Db2whc/index.html#getting_started){:new_window}.--> |
|  | HITRUST  | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | Db2 Hosted can be used today for HITRUST |
|  | International Organization for Standardization (ISO)  | Y | ISO 27001, 27002, 27017, and 27018 |
|  | Service Organization Controls (SOC) | Y | SOC 2 Type 2 |
|  | GDPR | Y | - |
|  | EU Cloud | Y | Use Frankfurt region. Support provided physically in EU. |
|  | Full list of compliances | Y | [Security compliances ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| Backup & restore | Daily backups | Y | 14 days of daily backups |
|  | Point-in-time self-serve recovery | Available Nov 15, 2018 | [Point-in-time restore](br.html#point-in-time) |
|  | Backups kept offsite | On request | As of Dec 1, 2018, offsite is default  |
|  | Keep backup up to 10 yrs | On request | As of Dec 1, 2018. Requires support ticket. |
|  | Query old data without restore | Y | Must set up [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| Networking, security, & VMs | Single-tenant virtual machine | Y | All paid plans, including Flex, are single-tenant VMs or baremetal. |
|  | ICIAE | Y | Request from IBM Support. If ICIAE is being requested for an existing service environment, your data must be migrated to your ICIAE environment by IBM Support. |
|  | VPN | Y | Request from IBM Support |
|  | On-disk encryption | Y | -  |
|  | SSL/TLS connections | Y | -  |
|  | IP whitelisting | Some | Available at Db2 user level. For network level, consider ICIAE or similar.  |
|  | Key Protect (Bring your own key) | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / Interconnected service | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Maximum concurrent connection limit: **Free plan** | Y | Max: 5 connections  |
|  | Maximum concurrent connection limit: **paid plans** | N | Unlimited number of connections  |
|  |  |  |  |
| Pricing & purchasing | BYOL discounts | Y | [Announcement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Available on IBM Cloud | Y | Both subscription and pay-as-you-go |
|  | Available with software quote order | Y | All plans including Flex. [Parts & details ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Available on Hybrid Data Management Platform (HDMP) | Y | Flex plan only. [Details about HDMP ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:new_window}|
|  | Daily billing | Y | Billing for Flex plans is based on peak daily usage. For example, if you scale up from 2 to 8 cores for one hour of a day, you will be billed for 8 cores for only that day, and 2 cores for all of the other days of the month. |
|  | Hourly billing | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | Main pricing metric | Monthly | Prices are stated in monthly terms (for example, $189 USD per month). A prorated monthly price is based on the number of days of activated service during the month in which the service was terminated. [Examples](plans_pricing.html) |
|  |  |  |  |
| Deployment & scaling durations | Dallas | **Deploy**: < 5 minutes. **Scale**: < 45 minutes. | Flex plan only, depending on inventory |
| | Other US South | **Deploy**: 1 day. **Scale**: 8 hours. | Some locations shorter than others |
| | Frankfurt & London | **Deploy**: < 5 min. **Scale**: 2 hours. | Flex plan only, depending on inventory |
| | Other EU | **Deploy**: 3-5 days. **Scale**: 1-2 days. | Some locations shorter than others |
| | Sydney | **Deploy**: < 1 hour. **Scale**: 2 hours. | Flex plan only, depending on inventory |
| | Other AP | **Deploy**: 3-5 days. **Scale**: 3-5 days. | Some locations shorter than others. Lower volumes in AP result in slower infrastructure provisioning times. |
{: caption="Table 1. Features and specifications supported in Db2 on Cloud" caption-side="top"}

