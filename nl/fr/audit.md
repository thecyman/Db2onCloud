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

# Audit
{: #audit}

Voici les méthodes qui vous permettent d'auditer l'activité de la base de données {{site.data.keyword.Db2_on_Cloud_short}} :

* [CHANGE HISTORY event monitor ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

En créant un moniteur d'événements CHANGE HISTORY, vous pouvez interroger la table du moniteur d'événements pour déterminer ce qui a été effectué dans la base de données et par qui. 

L'interrogation chronologique permet de stocker tous les changements apportés à vos données et même d'interroger vos anciennes données à un point précis dans le temps. Si vous souhaitez utiliser cette méthode d'audit, veillez à d'abord configurer vos tables pour la prise en charge de l'interrogation chronologique.

Pour plus d'informations sur ces méthodes d'audit, voir [How do I audit or track changes? ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.
