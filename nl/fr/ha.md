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

# Haute disponibilité (HA)
{: #ha}

Les plans haute disponibilité de {{site.data.keyword.Db2_on_Cloud_short}} ont d'excellentes caractéristiques en matière de disponibilité avec un niveau de service de 99,99 %. 
{: shortdesc}

Les plans haute disponibilité standard <!-- without a DR node -->offrent la reprise en ligne ainsi que des mises à jour en continu. Ils sont gérés à votre place grâce à la redirection automatique du client (ACR) et des adresses IP portables. 

La haute disponibilité avec un noeud de reprise après incident hors site est actuellement disponible en version bêta fermée. Contactez votre interlocuteur IBM si vous souhaitez avoir plus d'informations sur la participation à la version bêta fermée. Le noeud de reprise après incident vous permet de synchroniser rapidement vos données en temps réel avec un noeud de base de données situé à un emplacement hors site de votre choix. {{site.data.keyword.Db2_on_Cloud_short}} utilise la technologie Db2 HADR (High Availability Disaster Recovery) en mode ASYNC pour atteindre la capacité du noeud de reprise après incident hors site et fournit une fonction de lecture en veille sur ce noeud. 
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
