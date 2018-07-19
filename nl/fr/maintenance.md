---

copyright:
  years: 2014, 2018
lastupdated: "2018-05-10"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Politiques de maintenance et de notification

Les politiques de maintenance et de notification pour le service {{site.data.keyword.Db2_on_Cloud_long}} se trouvent sur la page [ des descriptions de service {{site.data.keyword.Bluemix_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){:new_window}. Des conditions d'utilisation supplémentaires spécifiques à {{site.data.keyword.Db2_on_Cloud_short}} sont présentées sous la catégorie **Chargeable additional SDs**. 

Une bonne connaissance de nos politiques peut vous aider à prévoir et planifier vos charges de travail afin d'obtenir de meilleurs comportements en cas de maintenance du système.
{: shortdesc}

## Politique de maintenance
{: #maintenance}

Depuis le 27 mars 2018, au cas où une maintenance du système planifiée doit être effectuée pour le service {{site.data.keyword.Db2_on_Cloud_short}}, les centres de données principaux (Londres, Dallas et Sydney) ne sont pas actualisés le même jour ouvrable. Tous les autres centres de données sont mis à jour simultanément un jour de la semaine qui ne correspond pas à celui utilisé par les centres de données principaux. Le tableau 1 montre un exemple de planification de la maintenance du système {{site.data.keyword.Db2_on_Cloud_short}}.

| Centre de données | Planification de la maintenance du système |
|-------------|-----------------------------|
| Londres | Lundi |
| Dallas | Mardi |
| Sydney | Mercredi |
| Tous les autres | Jeudi |
{: caption="Tableau 1. Exemple de planification d'une maintenance du système" caption-side="top"}


## Règle de notification
{: #notification}

Depuis le 27 mars 2018, une notification vous est envoyée deux jours ouvrables à l'avance pour vous avertir d'une  maintenance du système planifiée pouvant impacter votre service {{site.data.keyword.Db2_on_Cloud_short}}. 

Cette règle de  notification {{site.data.keyword.Db2_on_Cloud_short}} exclut le cas particulier de la détection d'une faille de sécurité qui doit être considérée comme une urgence et traitée aussi vite que possible. Dans ce cas, un préavis d'au moins 24 heures est donné, comme stipulé dans les descriptions de service {{site.data.keyword.Bluemix_notm}}.
