---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Sauvegarde et restauration
{: #bnr}

Dans le cas de plans payants, des sauvegardes chiffrées de la base de données sont effectuées quotidiennement. Une sauvegarde quotidienne est conservée pour chacun des 14 derniers jours.
{: shortdesc}

En supplément des sauvegardes standard, vous pouvez utiliser [Time Travel Query ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} pour conserver les données historiques à d'autres fins, comme l'interrogation instantanée d'anciennes données ou l'audit simplifié. Vous pouvez également effectuer vos propres exportations en utilisant IBM Data Studio ou tout autre outil Db2.
 
Pour plus d'informations sur les restaurations avec point de cohérence, voir [Restauration avec point de cohérence](#point-in-time).

Tous les plans payants utilisent généralement IBM Cloud Object Storage (COS) pour conserver les sauvegardes hors site dans trois différents centres de données. Toutefois, Sydney et certains centres de données de plus petite taille peuvent ne pas prendre en charge actuellement la réplication hors site avec IBM COS. Consultez la [documentation IBM COS](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-endpoints#endpoints) correspondant à votre région afin de déterminer quelles régions prennent en charge la réplication hors site.

Vous pouvez également utiliser l'[interface de ligne de commande IBM Lift ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.lift-cli.cloud.ibm.com/){:new_window} pour importer des données dans {{site.data.keyword.Db2_on_Cloud_short}}.

## Restauration avec point de cohérence
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} inclut désormais une fonction de restauration avec point de cohérence. A partir de vos sauvegardes, vous pouvez effectuer une restauration à un point temporel précis. Actuellement, pour la plupart des clients, vous devez demander au support d'activer cette fonction. Voir le calendrier de mise en oeuvre suivant.

Vous trouverez ci-dessous une liste présentant la disponibilité de la fonction de restauration avec point de cohérence :
- Centre de données Dallas - Fonction disponible actuellement dans les systèmes à serveur unique
- Tous les autres cas, notamment Europe et systèmes à haute disponibilité à Dallas - Demande d'activation de la fonction auprès du support. La mise en oeuvre complète dans tous les systèmes sera effective le 28 février 2019.
- Système IBM Cloud Dedicated - Disponible uniquement via un ticket de demande de service.

Vous trouverez ci-dessous des exemples sélectionnés de capture d'écran concernant l'interface utilisateur de la console Web dans lesquels l'opération de restauration avec point de cohérence est exécutée et sa progression est indiquée :

1. Sélectionnez la stratégie de restauration avec **point de cohérence** puis sélectionnez une date de point de cohérence à laquelle restaurer la base de données. Le processus de restauration avec point de cohérence sélectionne la sauvegarde la plus proche de la date de point de cohérence demandée parmi les sauvegardes effectuées au cours des deux dernières semaines. 

   Le processus de restauration avec point de cohérence invalide les sauvegardes précédemment conservées dont la date est ultérieure à la date de point de cohérence en raison d'une divergence dans la chronologie.
   {: note}

   ![Vue de la sélection mise en évidence de la stratégie de restauration avec point de cohérence](images/pit_restore_1.png)

2. Confirmez que vous souhaitez continuer en utilisant vos sélections de restauration. Une fois l'opération de restauration commencée, vous ne pouvez pas changer la demande.  
![Vue de la boîte de dialogue de confirmation de restauration avec point de cohérence](images/pit_restore_2.png)

3. Le processus de restauration est en cours d'initialisation.
![Vue de l'initialisation de la restauration avec point de cohérence](images/pit_restore_3.png)

4. Restauration de la base de données au niveau du point de cohérence sélectionné.
![Vue de la progression de la restauration avec point de cohérence](images/pit_restore_4.png)

5. Un nouveau point de sauvegarde est en cours de création. La base de données restaurée avec un point de cohérence est prête à être utilisée.
![Vue de la création du nouveau point de sauvegarde](images/pit_restore_5.png)

6. L'opération de restauration a abouti.
![Vue de l'opération de restauration terminée](images/pit_restore_6.png)

