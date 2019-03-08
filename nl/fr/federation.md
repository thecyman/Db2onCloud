---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-26"

keywords: 

subcollection: Db2onCloud

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

# Virtualisation de données (fédération)
{: #fed}

La virtualisation de données Db2 (qui porte également le nom de fédération) est prise en charge par {{site.data.keyword.Db2_on_Cloud_short}}. Elle vous donne un accès de requête unique à toutes vos données situées dans des bases de données réparties partout dans votre organisation. Vous pouvez accéder aux données qui se trouvent dans toutes vos sources de données Db2 ou Informix, aussi bien sur le cloud que sur site. 
{: shortdesc}

Cette fonction est prise en charge sur toutes les versions de {{site.data.keyword.Db2_on_Cloud_short}}, sauf sur le plan Lite gratuit. Vous pouvez toutefois utiliser ce dernier comme une cible depuis laquelle vous pouvez extraire les données.

## Cas d'utilisation
{: #use_cases}

### Consolidation des sources de données

En fédérant les sources de données qui se trouvent dans votre organisation, aussi bien sur le cloud que sur site, vos données virtualisées semblent être extraites depuis une source unique. La virtualisation des données élimine la nécessité de mettre en place un processus de migration lourd et coûteux, en vous donnant la possibilité d'analyser toutes vos données efficacement et pour un coût plus abordable.

<!-- A company may have started their operations with an on-premises Db2 server. As cloud technology becomes more widespread and companies start to operate on cloud in a cost-effective fashion, there will be continued Cloud growth. However, the organization’s data on both sources remain as a critical component to their decision-making processes. By way of example, a client operating in retail industry needs to be able to access all data, say customer information, to run further analysis on their customers’ consumption behaviors. They need to be able to identify customers, match their records on cloud with already existing ones from an on-premises database and compose them as if the data is being retrieved from a single source. Federation capability here prevents the burdensome data migration process and allows the user to access the data without moving the data.

located in the cloud and on-premises -->

### Association à Db2 Warehouse on Cloud

Les utilisateurs des produits de la famille Db2 peuvent fédérer des données depuis des bases de données {{site.data.keyword.Db2_on_Cloud_short}} et {{site.data.keyword.dashdbshort_notm}}. A partir d'une interface courante d'accès aux données, vous pouvez facilement ajouter et analyser vos données ou effectuer une requête sur ces dernières, sans avoir à mettre en oeuvre des processus ETL complexes ou à ajouter du code supplémentaire.

<!-- Db2 family users would now be able to federate data between Db2 on Cloud and Db2 Warehouse on Cloud. By being provided a common interface for accessing the data, a user can now easily add or query data from or to the Warehouse without complex ETL processes or any additional code. -->

### Données partitionnées sur des serveurs multiples

Parfois, il peut vous sembler opportun de partitionner vos données. Avec les fonctionnalités de fédération, des requêtes peuvent être effectuées sur les données partitionnées avec une interface unifiée. La fédération vous permet de mieux équilibrer vos charges de travail, de mettre à l'échelle des parties spécifiques d'une application et de créer des microservices qui fonctionnent ensemble. 

<!-- At times, users may choose to partition (shard). With federation capabilities, data can be queried with a unified interface and this lets the user better balance the workload, scale specific parts of an app or create microservices that work together. -->

### Augmentation de la capacité d'une base de données au-delà des limites fixées

La fédération vous permet d'accroître la capacité d'une base de données sur site en la fédérant avec une base de données sur le cloud. La virtualisation des données est une option très intéressante si votre base de données sur site ne dispose plus de suffisamment de capacité de stockage. L'augmentation de la capacité d'une base de données via la fédération est utile pour un nouveau développement, car les développeurs n'ont pas besoin de modifier une base de données qui se trouve déjà en production. Vous pouvez aussi choisir d'effectuer une fédération entre deux bases de données {{site.data.keyword.Db2_on_Cloud_short}} pour augmenter la capacité de ces bases de données au-delà des limites du plan Flex.

<!-- By using federation, users can increase capacity of an on premises database by federating to or from the cloud. This is a great option if your on premises database is running out of storage. Increased capacity will also be useful for new development as our users no longer need to change a database in production. You can also use this feature to federate between two Db2 on Cloud databases to increase the capacity beyond the current limits of the Flex plan. -->

## Initiation
{: #getting_started}

L'exemple de procédure ci-dessous vous montre comment fédérer vos sources de données disparates afin que les données semblent extraites d'une source unique. Il illustre la fédération de deux bases de données {{site.data.keyword.Db2_on_Cloud_short}} :

### Sur la machine cible Db2 on Cloud
{: #targ}

Nom d'hôte : targetdotcom

1. Créez une table `testdata` dans le schéma `admin2`.

2. A partir de la console {{site.data.keyword.Db2_on_Cloud_short}}, chargez la table `testdata` en tant qu'utilisateur `admin2` avec le mot de passe `YYYY`.

<!-- ### On a client machine of the target

1. Catalog the target machine:<br/>
   `db2 catalog tcpip node <node_name> remote <host_name> server 50000`<br/>

   For example:<br/>
   `db2 catalog tcpip node fedS remote targetdotcom server 50000`

2. Catalog the database on fedS:<br/>
   `db2 catalog db bludb as <db_name> at node <node_name>`

   For example:<br/>
   `db2 catalog db bludb as srcdb at node fedS`

3. Connect to the database on fedS:<br/>
   `db2 connect to <catalog_db_name> user <admin_user> using '<admin_password>'`

   For example:<br/>
   `db2 connect to srcdb user 'admin1' with password 'XXXX'`

4. Create a wrapper on fedS:<br/>
   `db2 "create wrapper drda"`

5. Create a server to talk to the target machine:<br/>
   `db2 "create server <server_name> type dashdb version 11 wrapper drda authorization \"<admin_user_on_target>\" password \"<admin_password_on_target>\" options (host '<target_host_name>', port '50000', dbname 'bludb')"`

   For example:<br/>
   `db2 "create server db2server type dashdb version 11 wrapper drda authorization \"admin2\" password \"YYYY\" options (host 'targetdotcom', port '50000', dbname 'bludb')"`

6. Create the user mapping for admin2:<br/>
   `db2 "create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')"`

   For example:<br/>
   `db2 "create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')"`

7. Create a nickname for the database:<br/>
   `db2 -v "create nickname <nickname> for <server_name>.<schema_name>.<table_name>"`

   For example:<br/>
   `db2 -v "create nickname ntest1 for db2server.admin2.testdata"`

### On the Db2 on Cloud source machine

1. Test that you can pull data from the target server:<br/>
   `db2 "select * from <nickname>"`

   For example:<br/>
   `db2 "select * from ntest1"`
-->

### Sur une machine Db2 on Cloud utilisée en tant que source de la fédération
{: #fed_src}

A partir de la console {{site.data.keyword.Db2_on_Cloud_short}} :

1. Créez un serveur pour parler à la machine cible :<br/>
   `create server <server_name> type dashdb version 11 wrapper drda authorization "<admin_user_on_target>" password "<admin_password_on_target>" options (host '<target_host_name>', port '50000', dbname 'bludb')`

   Exemple :<br/>
   `create server db2server type dashdb version 11 wrapper drda authorization "admin2" password "YYYY" options (host 'targetdotcom', port '50000', dbname 'bludb')`

2. Créez le mappage utilisateur pour admin2 :<br/>
   `create user mapping for <admin_user> server db2server options (remote_authid '<admin_user_on_target>', remote_password '<admin_password_on_target>')`

   Exemple :<br/>
   `create user mapping for admin1 server db2server options (remote_authid 'admin2', remote_password 'YYYY')`

3. Créez un alias pour la base de données :<br/>
   `create nickname <nickname> pour <server_name>.<schema_name>.<table_name>`

   Exemple :<br/>
   `create nickname ntest1 for db2server.admin2.testdata`

4. Testez le fait que vous puissiez extraire des données du serveur cible :<br/>
   `select * from <nickname>`

   Exemple :<br/>
   `select * from ntest1`

## Informations complémentaires
{: #more_info}

Pour plus d'informations sur la virtualisation des données (fédération), voir : [Federation ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/fcontainer.html){:new_window}.

Par défaut, {{site.data.keyword.Db2_on_Cloud_short}} prend en charge Informix et Db2 (y compris Db2 et Db2 Warehouse sur site). La prise en charge de certaines sources de données devra peut-être être installée par le support IBM sur demande. Pour plus d'informations sur les sources de données prises en charge par la fédération, voir : [Federation Supported Data Sources ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/docview.wss?uid=swg27050561){:new_window}.

