---

copyright:
  years: 2014, 2018
lastupdated: "2018-10-26"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
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
|  | Data center location options | Y | [Locations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-locations){:new_window} |
|  | BLU in-memory | Y | Default is row, specify `CREATE TABLE..AS COL` for BLU |
|  | Activity Tracker | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Root access provided | N | Use Db2 Hosted if root access is required |
|  |  |  |  |
| High availability & replication | Offsite DR | Y | - |
|  | High availability (2 nodes in 1 zone) | Y | 99.99% uptime SLA |
|  | Different zones in same data center | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Change Data Capture (CDC) | Y | - |
|  | Use as HADR from on premises | N | Use CDC. For information, see [How can I migrate or sync data from Db2 to Db2 on Cloud? ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Autonomous failover - HA | Y | - |
|  | Autonomous failover - Offsite DR | N | Use button or API |
|  | IP moves with failover | Y | Local HA only; not offsite HADR |
|  |  |  |  |
| Maintenance policies & SLAs | High availability plans | 99.99% | - |
|  | Single server plans | 99.9% | - |
|  | Offsite DR node | 99.9% | Must use additional local HA to achieve 99.99% |
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
|  | Point-in-time self-serve recovery | Available Nov 15, 2018 | - |
|  | Backups kept offsite | On request | As of Dec 1, 2018, offsite is default  |
|  | Keep backup up to 10 yrs | On request | As of Dec 1, 2018. Requires support ticket. |
|  | Query old data without restore | Y | Must set up [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| Networking, security, & VMs | Single-tenant virtual machine | Y | All paid plans, including Flex, are single-tenant VMs or baremetal. |
|  | ICIAE | Y | Request from IBM Support. If ICIAE is added to existing server, your server must be migrated to your ICIAE environment by IBM support. |
|  | VPN | Y | Request from IBM Support |
|  | On-disk encryption | Y | -  |
|  | SSL/TLS connections | Y | -  |
|  | KeyProtect (Bring your own key) | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / Interconnected service | [In roadmap ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  |  |  |  |
| Pricing & purchasing | BYOL discounts | Y | [Announcement ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Available via IBM Cloud | Y | Both subscription and pay-as-you-go |
|  | Available via software quote order | Y | All plans including Flex. [Parts & details. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
{: caption="Table 1. Features and specifications supported in Db2 on Cloud" caption-side="top"}

