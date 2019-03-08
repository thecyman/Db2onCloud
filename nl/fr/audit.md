---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# Audit, consignation et surveillance
{: #aud-log-mon}

## Audit
{: #auditing}

Vous pouvez créer une règle d'audit de base de données qui vous permet d'effectuer l'audit des différentes catégories des événements stockés dans les tables d'événement d'audit de votre base de données. Pour plus d'informations, voir [Audit policy guidelines ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}.

Vous pouvez également effectuer l'audit et le suivi des modifications apportées à votre base de données en utilisant les méthodes suivantes :
* En créant un moniteur d'événements `CHANGE HISTORY`, vous pouvez interroger la table du moniteur d'événements pour déterminer ce qui a été effectué dans la base de données et par qui. Pour plus d'informations, voir [`CHANGE HISTORY` event monitor ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}.
* L'interrogation chronologique permet de stocker tous les changements apportés à vos données et même d'interroger vos anciennes données à un point précis dans le temps. Si vous souhaitez utiliser cette méthode d'audit, veillez à d'abord configurer vos tables pour la prise en charge de l'interrogation chronologique. Pour plus d'informations, voir [Time Travel Query ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}.

Pour plus d'informations sur l'audit et sur le suivi des modifications apportées à la base de données, voir [How do I audit or track changes? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Consignation et surveillance
{: #log_mon}

La surveillance et la consignation sont des opérations faisant partie du service. Toutefois, elles ne sont pas directement accessibles pour l'utilisateur final. A la place, l'infrastructure est utilisée par le personnel opérationnel IBM pour traiter les problèmes éventuels.  

Pour connaître la disponibilité d'Activity Tracker, voir la page présentant la [feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window}.

Vous pouvez vous connecter en utilisant un client de ligne de commande Db2 (CLPPlus, par exemple) pour accéder aux informations détaillées et aux diagnostics.

### Présentation générale
{: #basic_overview}

Il existe deux types de vérification de base : vérifications d'intégrité/de disponibilité externes et surveillance à l'aide de mesures. IBM surveille des centaines de mesures et stocke ces dernières de manière historique. En fonction de leurs valeurs, des alertes sont générées. Ces dernières sont envoyées au personnel opérationnel IBM. Ainsi, il est garanti qu'elles sont vues et traitées. En outre, IBM envoie les journaux de diagnostic et de système d'exploitation archivés pour un diagnostic rapide. {{site.data.keyword.Db2_on_Cloud_short}} est conforme au règlement RGPD. De plus, les options IBM EU Cloud permettent d'appliquer de manière encore plus stricte ce règlement, si nécessaire.


