---

copyright:
  years: 2014, 2018
lastupdated: "2018-11-01"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Fonctions & spécifications
{: #overview}

Les fonctions et spécifications {{site.data.keyword.Db2_on_Cloud_long}} sont répertoriées ici pour votre commodité.
{: shortdesc}

| Catégorie | Fonction | Pris en charge ? | Commentaires |
|----------|---------|------------|----------|
| Général | Db2 AESE | O | Db2 v11.1.3.3 |
|  | Lecture en veille | O | Noeud DR hors site seulement |
|  | Mises à jour en continu automatiques | O | Avec plans haute disponibilité |
|  | Options d'emplacement de centre de données | O | [Emplacements ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-locations){:new_window}. Voir aussi : Durées de déploiement et de mise à l'échelle. |
|  | BLU en mémoire | O | La valeur par défaut est la ligne, indiquer `CREATE TABLE..AS COL` pour BLU |
|  | Activity Tracker | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Droits d'accès de l'utilisateur root fournis | N | Utiliser Hébergé Db2 si des droits d'accès de l'utilisateur root sont obligatoires |
|  |  |  |  |
| Haute disponibilité & réplication | DR hors site | O | - |
|  | Haute disponibilité (2 noeuds dans 1 zone) | O | 99,99 % disponibilité SLA |
|  | Différentes zones dans même centre de données | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Cache de données de calcul (CDC) | O | - |
|  | Utilisation en tant que fonction de reprise sur sinistre haute disponibilité sur site | N | Utiliser CDC. Pour plus de détails, voir [How can I migrate or sync data from Db2 to Db2 on Cloud? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Basculement autonome - Haute disponibilité| O | - |
|  | Basculement autonome - DR hors site | N | Utiliser bouton ou API |
|  | Déplacements IP avec basculement | O | Haute disponibilité local seulement ; pas de HADR hors site |
|  |  |  |  |
| Règles de maintenance & SLA | Plans à haute disponibilité | 99,99 % | - |
|  | Plans à serveur unique | 99,5 % | - |
|  | Noeud DR hors site | 99,5 % | Doit utiliser une haute disponibilité supplémentaire pour atteindre 99,99 % |
|  | Politique de maintenance | O | [Lire les détails ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| Conformités à la sécurité | Prêt pour la loi HIPAA | O | Tous les plans payants y compris Flex. Doit demander le mode HIPAA auprès du support IBM. <!--For Db2 Warehouse on Cloud [see docs here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Db2whc/index.html#getting_started){:new_window}.--> |
|  | HITRUST  | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | Hébergé par Db2 peut être utilisé aujourd'hui pour HITRUST |
|  | International Organization for Standardization (ISO)  | O | ISO 27001, 27002, 27017 et 27018 |
|  | SOC (Service Organization Controls) | O | SOC 2 Type 2 |
|  | GDPR | O | - |
|  | Cloud EU | O | Utiliser région de Francfort. Support physique proposé en Europe. |
|  | Liste complète des conformités | O | [Conformités de sécurité ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| Sauvegarde & restauration | Sauvegardes quotidiennes | O | 14 jours de sauvegardes quotidiennes |
|  | Reprise en libre service ponctuelle | Disponible le 15 nov 2018 | - |
|  | Sauvegardes conservées hors site | A la demande | Hors site par défaut au 1er déc 2018  |
|  | Conservation de sauvegarde jusqu'à 10 ans | A la demande | Dès le 1er déc 2018. Requiert un ticket de demande de service. |
|  | Interrogation d'anciennes données sans restauration | O | [Time Travel Query ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} doit être configuré |
|  |  |  |  |
| Réseau, sécurité & machines virtuelles | Machine virtuelle à service exclusif | O | Tous les plans payants, y compris Flex, sont des machines virtuelles à service exclusif ou bare metal. |
|  | ICIAE | O | Demande du support IBM. Si ICIAE est demandé pour un environnement de service existant, vos données doivent être migrées vers votre environnement ICIAE par le support IBM. |
|  | VPN | O | Demande du support IBM |
|  | Chiffrement sur disque | O | -  |
|  | Connexions SSL/TLS | O | -  |
|  | Placement sur liste blanche IP | Certaines | Disponible au niveau utilisateur Db2. Pour le niveau réseau, pensez à ICIAE ou similaire. |
|  | KeyProtect (Bring your own key) | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / Service interconnecté | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  |  |  |  |
| Tarification & achat | Remises BYOL | O | [Annonce ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Disponible via IBM Cloud | O | A la fois Abonnement et Paiement à la carte |
|  | Disponible via commande devis logiciel | O | Tous les plans y compris Flex. [Parts & details. ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Facturation quotidienne | O | La facturation pour les plans Flex repose sur une utilisation quotidienne aux heures pleines. Par exemple, si vous passez de 2 à 8 coeurs pour une heure d'un jour, vous serez facturé pour 8 coeurs pour uniquement ce jour, et 2 coeurs pour tous les autres jours du mois. |
|  | Facturation horaire | [Dans la feuille de route ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | Grille tarifaire principale | Mensuelle | Les prix sont définis sur une base mensuelle (par exemple, 189 dollars américains par mois). Un prix mensuel au prorata repose sur le nombre de jours de service activé pendant le mois au cours duquel le service a été interrompu. [Exemples](plans_pricing.html) |
|  |  |  |  |
| Durées de déploiement & de mise à l'échelle | Dallas | **Déploiement **: < 5 minutes. **Mise à l'échelle **: < 45 minutes. | Plan Flex seulement, selon le stock |
| | Autre Sud des Etats-Unis | **Déploiement **: 1 jour. **Mise à l'échelle **: 8 heures. | Certains emplacements plus courts que d'autres |
| | Francfort & Londres | **Déploiement **: < 5 minutes. **Mise à l'échelle **: 2 heures. | Plan Flex seulement, selon le stock |
| | Autre EU | **Déploiement**: 3-5 jours. **Mise à l'échelle **: 1-2 jours. | Certains emplacements plus courts que d'autres |
| | Sydney | **Déploiement **: < 1 heure. **Mise à l'échelle **: 2 heures. | Plan Flex seulement, selon le stock |
| | Autre Asie-Pacifique | **Déploiement**: 3-5 jours. **Mise à l'échelle **: 3-5 jours. | Certains emplacements plus courts que d'autres. Des volumes plus faibles en Asie-Pacifique se traduisent par des délais de mise à disposition d'infrastructure plus lents. |
{: caption="Table 1. Fonctions et spécifications prises en charge dans Db2 on Cloud" caption-side="top"}

