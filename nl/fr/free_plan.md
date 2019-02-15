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

# Plan gratuit
{: #free_plan}

Le plan gratuit {{site.data.keyword.Db2_on_Cloud_long}} fournit des ressources de base qui vous permettent de développer ou d'en apprendre davantage sur Db2, sans frais.
{: shortdesc}

Le plan gratuit n'est soumis à aucune limite dans le temps, mais les utilisateurs doivent prolonger leur plan gratuit tous les 30 jours.

Seul le support de la communauté est disponible. 
 
## Architecture
{: #architecture}

A la différence des autres plans {{site.data.keyword.Db2_on_Cloud_short}}, le plan gratuit {{site.data.keyword.Db2_on_Cloud_short}} s'exécute sur un système à service partagé. Les plans Flex et Precise Performance s'exécutent sur leurs propres machines virtuelles à service exclusif ou des serveurs bare metal.
 
Le plan gratuit vous permet d'utiliser un schéma de base de données.

Pour plus d'informations sur le plan gratuit {{site.data.keyword.Db2_on_Cloud_short}}, voir [FAQ ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oc_free_plan_faq){:new_window}.

## Utilisation du plan gratuit en dehors de l'Amérique du Nord continentale
{: #outside_na}

Le plan gratuit est accessible actuellement sans carte de crédit pour l'Amérique du Nord continentale. En dehors de cette zone géographique, les clients doivent ajouter une carte de crédit dans leur compte IBM Cloud puis sélectionner la région "Sud des Etats-Unis" pour que le plan gratuit soit visible et puisse être sélectionné.

Ce plan est toujours gratuit et votre carte de crédit ne sera pas débitée.

## Restrictions du plan gratuit
{: #fp_restrictions}

Il est fortement recommandé d'utiliser un plan de service de niveau d'entreprise et non un plan de service gratuit pour les charges de travail sensibles aux performances ou stratégiques.
{: important}

La tableau suivant présente les restrictions du plan de service gratuit {{site.data.keyword.Db2_on_Cloud_short}} :

| Catégorie | Elément | Restriction | 
|----------|------|-------------|
| Ressources | Stockage | 200 Mo de stockage par utilisateur |
|  | Connexions | 5 connexions par utilisateur |
|  | Performances | Les performances peuvent varier car des charges de travail peuvent être exécutées par d'autres utilisateurs sur le système à service partagé |
|  |  |
| Fonctions | Fédération | Pas de prise en charge |
|  | Compatibilité Oracle | Pas de prise en charge |
|  | Extensions définies par l'utilisateur (UDF) | Aucune prise en charge sur les plans {{site.data.keyword.Db2_on_Cloud_short}}, y compris le plan gratuit |
|  | Gestion des utilisateurs | L'utilisateur ne dispose pas de droits d'administration |
|  | Contrôle d'accès aux lignes et aux colonnes (RCAC) | Pas de prise en charge |
|  | IBM InfoSphere Data Replication à utiliser lors du chargement de données | Pas de prise en charge |
|  |  |
| Environnement réseau | IBM Cloud Integrated Analytics | Pas de prise en charge |
|  | IBM Cloud Dedicated | Pas de prise en charge |
|  |  |
| Conformités à la sécurité | Loi Health Information Portability and Accountability Act de 1996 (HIPAA) | Pas de prise en charge. Consultez la description de service. |
|  | Règlement général sur la protection des données (RGPD) européen | Pas de prise en charge. Consultez la description de service. |
|  |  |
| Gestion des comptes | Réactivation | La réactivation doit être effectuée tous les 30 jours. Si cette action n'est pas effectuée, les services de plan gratuit sont supprimés 60 jours après.  |
{: caption="Tableau 1. Restrictions du plan gratuit {{site.data.keyword.Db2_on_Cloud_short}}" caption-side="top"}


