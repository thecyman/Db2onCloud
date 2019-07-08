---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Politiques de maintenance et de notification
{: #maint_note_pol}

Les politiques de maintenance et de notification pour le service {{site.data.keyword.Db2_on_Cloud_long}} sont disponibles sur la page [des descriptions du service {{site.data.keyword.Bluemix_notm}}](http://www.ibm.com/software/sla/sladb.nsf/sla/bm?OpenDocument){:external}. Des conditions d'utilisation supplémentaires spécifiques à {{site.data.keyword.Db2_on_Cloud_short}} sont présentées sous la catégorie **Chargeable additional SDs**. 

Une bonne connaissance de nos politiques peut vous aider à prévoir et planifier vos charges de travail afin d'obtenir de meilleurs comportements en cas de maintenance du système.
{: shortdesc}

## Politique de maintenance
{: #maintenance}

Depuis le 27 mars 2018, au cas où une maintenance du système planifiée doit être effectuée pour le service {{site.data.keyword.Db2_on_Cloud_short}}, les centres de données principaux (Londres, Dallas et Sydney) ne sont pas actualisés le même jour ouvrable. Tous les autres centres de données sont mis à jour simultanément un jour de la semaine qui ne correspond pas à celui utilisé par les centres de données principaux. Le tableau 1 montre un exemple de planification de la maintenance du système {{site.data.keyword.Db2_on_Cloud_short}}.

| Centre de données | Planification exemple d'une maintenance possible |
|-------------|-----------------------------|
| Londres | Lundi |
| Dallas | Mardi |
| Sydney | Mercredi |
| Tous les autres | Jeudi |
{: caption="Tableau 1. Exemple de planification d'une maintenance du système" caption-side="top"}

Ce tableau ne constitue aucunement une planification de maintenance système officielle mais un exemple de planification de maintenance possible qui présente comment cette opération peut être effectuée différents jours pour une mise à jour spécifique.
{: note}

## Règle de notification
{: #notification}

Depuis le 27 mars 2018, une notification vous est envoyée deux jours ouvrables à l'avance pour vous avertir d'une maintenance du système planifiée pouvant impacter votre service {{site.data.keyword.Db2_on_Cloud_short}}. 

Cette règle de notification {{site.data.keyword.Db2_on_Cloud_short}} exclut le cas particulier de la détection d'une faille de sécurité qui doit être considérée comme une urgence et traitée aussi vite que possible. Dans ce cas, un préavis d'au moins 24 heures est donné, comme stipulé dans les descriptions de service {{site.data.keyword.Bluemix_notm}}.
