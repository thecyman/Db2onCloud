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

# Acerca de Db2 on Cloud
{: #overview}

{{site.data.keyword.Db2_on_Cloud_long}} es un servicio de base de datos SQL completamente gestionado. La consola web de {{site.data.keyword.Db2_on_Cloud_short}} facilita la ejecución de tareas comunes, como importar hojas de cálculo, ejecutar sentencias SQL y supervisar el servicio.
{: shortdesc}

## ¿Qué se incluye en el servicio gestionado?
{: #managed_service}

El servicio completamente gestionado de {{site.data.keyword.Db2_on_Cloud_short}} se despliega con unas pocas pulsaciones y le permite ejecutar su base de datos sin dificultad. Está optimizado para el usuario. El servicio gestiona automáticamente las actualizaciones del software subyacente y los problemas de hardware. El servicio incluye supervisión de estado de tipo 24x7 de la base de datos y de la infraestructura. Los datos del disco están cifrados y las conexiones con la base de datos se realizan con un sistema de seguridad mejorado. Los planes de alta disponibilidad ofrecen constantes actualizaciones continuas y puede escalar las apps sin incurrir en tiempo de inactividad. Para obtener más información, consulte [Alta disponibilidad](../Db2onCloud/ha.html){:new_window}.
{: shortdesc}




<!-- ## User management
{: #user_mgmt}

Management of users that were given access to the database is the sole responsibility of the user or users with the administrator role. The administrator has the responsibility to manage how other users in your organization access your database.
{: shortdesc}

The database administrator role manages the following types of user access: 
* Web console. From the web console, users can run queries against the database.
* Database. The administrator can grant granular access permissions to the database, including only being able to access certain tables, schemas, or even rows or columns. 

For more information about user management, see [Database user management ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/user_mgmnt.html){:new_window}

## Flexible scaling
{: #scale}

Independent scaling of RAM, storage, and compute cores. 
{: shortdesc}

Before provisioning your Flex system, you adjust your anticipated RAM, storage, and compute cores, then submit your choices.

After your system is provisioned and whenever your needs change, you can adjust your RAM, storage, and compute cores up or down. These dynamic adjustments typically take less than 20 minutes to complete. You can even scale CPU and RAM without any downtime by following these [guidelines ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/381931/how-can-i-scale-cpu-up-and-down-without-downtime-o.html){:new_window}.

## Backup and restore
{: #br}

Encrypted backups on the full Db2 managed service database are done daily. The last 14 daily backup snapshots are retained.
{: shortdesc}

Retained backups are used exclusively by IBM for only system recovery purposes in the event of a disaster or system loss. A request to restore your database from a backup is not supported. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. You can also perform your own exports using IBM Data Studio or any Db2 tool.

To store your backups at a remote storage site, make a request to IBM Support.

## High availability (HA)
{: #ha}

{{site.data.keyword.Db2_on_Cloud_short}} high availability plans have excellent availability characteristics with a 99.99% SLA. Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. 
{: shortdesc}

The standard high availability plans without a DR node provide seamless failover and rolling updates are managed for you by using automatic client reroute (ACR) and portable IPs.

High availability with a DR node gives you the ability to rapidly synchronize your data in real time to a database node that you can use as a failover node. {{site.data.keyword.Db2_on_Cloud_short}} uses the Db2 High Availability Disaster Recovery (HADR) technology in ASYNC mode to achieve the offsite DR node capability.

## Audit
{: #audit}

The following are methods by which you can audit activity on the {{site.data.keyword.Db2_on_Cloud_short}} database:

* [CHANGE HISTORY event monitor ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

By creating a CHANGE HISTORY event monitor, you can query the event monitor table to determine what was done within the database and by whom. 

The Time Travel Query makes it easy to store all of the changes to your data and even query your old data based on a selected point in time. To use this audit method, ensure that you first set up your tables to support Time Travel Query.

For more information about these audit methods, see [How do I audit or track changes? ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Plans and configurations
{: #plans_cfgs}

You can choose a {{site.data.keyword.Db2_on_Cloud_short}} plan that is configured and optimized for the work that you need to do:
{: shortdesc}

   * An entry plan to try things out (Precise Performance 500 (2.8.500))
   * A Flex plan in which you can independently scale RAM, storage, and compute resources
   * Small, medium, and large plans for production
   * Plans configured for High Availability or for Oracle compatibility
   * And more ...

View available plans in the {{site.data.keyword.Bluemix}} catalog:
   * Plans configured for high-speed, online transaction processing (OLTP): [{{site.data.keyword.Db2_on_Cloud_short}}](https://console.ng.bluemix.net/catalog/services/dashdb-for-transactions-sql-database){:new_window}

If you don't see a configuration in the catalog that you need, contact [{{site.data.keyword.IBM_notm}} Sales ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/connect/ibm/us/en/?lnk=fcw){:new_window} to discuss other options.

## Loading data
{: #load}

You can load data from a data file in a delimited format such as CSV or TXT located on a local network, an object store (Amazon S3 or IBM Cloud Object Storage (formerly SoftLayer Swift)), or a Db2® server. You can also populate a database instance with data directly from a Cloudant® database or by performing a load process from an application such as InfoSphere® DataStage®.
{: shortdesc}

* [Loading data from Oracle ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading data from SQL Server ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading a CSV file ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://lift.ng.bluemix.net/#docs){:new_window}
* [Loading data from Amazon S3 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/s3.html){:new_window}
* [Loading data from IBM Cloud Object Storage (formerly SoftLayer Swift) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/loaddata_swift.html){:new_window} -->

<!--* [Loading data from PureData System for Analytics (Netezza) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://lift.ng.bluemix.net/#docs){:new_window} -->

<!-- ## Connecting
{: #connect}

You can connect command-line interfaces, IBM® or third-party applications or tools, or apps that you create to your Db2® database. 
{: shortdesc}

### Prerequisites
{: #connect_prereq}

Before you can connect to your Db2 managed service database, complete the [prerequisites ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connecting_applications_to_dashdb_database.html){:new_window}.
{: shortdesc}

### Configuring your environment
{: #cfg_env}

To connect local applications and tools to your Db2 database, you need to [configure your environment ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_driver_package_config.html){:new_window}. 
{: shortdesc}

### Connecting programmatically
{: #conx_prgrm}

You can use common programming languages to create applications that connect to a Db2 database.
{: shortdesc}

* [JDBC ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_jdbc_applications.html){:new_window}
* [ODBC ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cli_and_odbc_applications.html){:new_window}
* [.NET ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting__net_applications.html){:new_window}
* [PHP ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_php.html){:new_window}

### Connecting apps and tools
{: #conx_apps_tools}

You can also connect external applications and tools to {{site.data.keyword.dashdbshort_notm}} and use them to further manage or analyze your data. For example:
   * Connect your {{site.data.keyword.Bluemix_short}} applications that need a transactional database.
   * [Connect {{site.data.keyword.IBM_notm}} InfoSphere® Data Architect to design and deploy your database schema. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_ibm_data_architect.html){:new_window} -->
<!--   * Connect Esri ArcGIS to perform geospatial analytics and map publishing with your data. -->
<!--   * [Connect an {{site.data.keyword.IBM_notm}} Cognos® server to run Cognos reports against your data. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_cognos.html){:new_window}
   * Connect SQL-based tools such as Tableau or Microsoft Excel to manipulate, analyze, or visualize your data. 
       * [Tableau ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_tableau.html){:new_window}
       * [Microsoft Excel ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_excel.html){:new_window} -->
<!--   * [Connect Aginity Workbench to migrate Netezza® data models and data to {{site.data.keyword.dashdbshort_notm}}. ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/connecting/connect_connecting_aginity.html){:new_window} -->

<!-- ## Local development environment
{: #local_dev}

If you want to set up a local Db2 development environment, you can use either of the following:

* [IBM Db2 Developer Community Edition ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/ibm-db2-direct-and-developer-editions){:new_window} Free. Includes all Db2 features, but only for development use.
* [IBM Db2 Express-C ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/developerworks/downloads/im/db2express/){:new_window} Free. A limited version of Db2 that is free for any use, including production or embedded systems.
{: shortdesc}

## Communities
{: #communities}

There are user-driven communities that you can join for information, tutorials, discussions, and help from professional Db2 users. And it's free to join!
{: shortdesc}

* [International Db2 Users Group (IDUG) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.idug.org/){:new_window} IDUG® is an independent, not-for-profit, user-run organization whose mission is to support and strengthen the information services community by providing the highest quality education and services designed to promote the effective utilization of Db2.
* [Db2 Community on developerWorks ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/data/db2/){:new_window} A Db2 developer community.
* [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://stackoverflow.com/users/login?ssrc=anon_ask&returnurl=https%3a%2f%2fstackoverflow.com%2fquestions%2fask%3ftags%3ddashdb){:new_window} A support forum and community for developers. -->

