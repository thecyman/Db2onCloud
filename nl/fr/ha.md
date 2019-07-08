---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-22"

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

# Haute disponibilité (HA)
{: #ha}

Les plans de haute disponibilité de {{site.data.keyword.Db2_on_Cloud_short}} ont d'excellentes caractéristiques en matière de disponibilité avec un niveau de service de 99,99 %. 
{: shortdesc}

Les plans de haute disponibilité standard sans noeud de reprise après incident offrent la reprise en ligne ainsi que des mises à jour en continu. Ils sont gérés à votre place grâce à la redirection automatique du client (ACR) et des adresses IP portables.

En outre, vous pouvez ajouter un noeud de reprise après incident géorépliqué. Cette option de noeud de reprise après incident hors site vous permet de synchroniser rapidement vos données en temps réel avec un noeud de base de données situé dans un centre de données {{site.data.keyword.Bluemix_notm}} hors site de votre choix. 

[Liste des emplacements de centre de données où des noeuds de reprise après incident sont disponibles.](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:external}

{{site.data.keyword.Db2_on_Cloud_short}} utilise la technologie Db2 HADR (High Availability Disaster Recovery) en mode `ASYNC` pour atteindre la capacité du noeud de reprise après incident hors site et fournit une `fonction de lecture en veille` sur ce noeud.

## **Brésil : Règle supplémentaire 14** (concerne les systèmes mis à disposition pour le gouvernement fédéral brésilien)
{: #rule_14}

A ce stade, l'option de reprise après incident pour les offres Db2 on Cloud n'est pas disponible au Brésil pour le gouvernement fédéral en raison de la Règle supplémentaire 14.

## Ajout d'un noeud de reprise après incident géorépliqué
{: #add_dr}

Pour les utilisateurs {{site.data.keyword.Db2_on_Cloud_short}} existants :
 * Vous pouvez ajouter un noeud de reprise après incident à la demande à des instances {{site.data.keyword.Db2_on_Cloud_short}} existantes. Après avoir cliqué sur votre instance dans le tableau de bord {{site.data.keyword.Bluemix_notm}}, vous verrez s'afficher une option appelée **Manage Disaster Recovery**. Vous pouvez ajouter un noeud de reprise après incident géorépliqué à partir de cet endroit.
 * Si vous avez acheté {{site.data.keyword.Db2_on_Cloud_short}} sur contrat via un ingénieur commercial et que vous n'avez pas d'abonnement {{site.data.keyword.Bluemix_notm}}, contactez votre interlocuteur IBM pour ajouter un noeud de reprise après incident.

Si vous n'êtes pas un utilisateur {{site.data.keyword.Db2_on_Cloud_short}} actuellement :
 * Commandez {{site.data.keyword.Db2_on_Cloud_short}} via {{site.data.keyword.Bluemix_notm}}, ou prenez contact avec votre ingénieur commercial.
 * Vous pouvez ensuite ajouter un noeud de reprise après incident à l'aide de l'option **Manage Disaster Recovery** de la console.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## Gestion de la haute disponibilité et des noeuds de reprise après incident
{: #manage_ha_dr}

Pour les noeuds haute disponibilité standard qui ne sont pas hors site, le basculement est géré automatiquement pas IBM. IBM surveille la santé de votre serveur, le basculement et la reprise par restauration si nécessaire, notamment les mises à jour en continu et la mise à l'échelle pour que la disponibilité soit aussi élevée que possible.

Pour la reprise après incident géorépliquée (HADR), vous devez effectuer un basculement manuel à l'aide de l'option **Manage Disaster Recovery** de la console. En outre, vous pouvez effectuer le basculement à l'aide d'une API, comme décrit [ici](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:external}.

## Foire aux questions
{: #faq}

### Quelles sont les modifications requises pour une application qui utilise Db2 afin qu'elle fonctionne avec le noeud de reprise après incident après la reprise ? Est-ce que le nom DNS ou l'adresse IP change après la reprise ?

**R** : Non. Deux noms d'hôte qui peuvent être résolus vous sont affectés. Si votre application est configurée pour utiliser Db2 ACR (Active Connection Reroute), elle est alors réacheminée vers le noeud principal.

Pour plus d'informations sur le noeud de reprise après incident géorépliqué, cliquez [ici](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:external}.
