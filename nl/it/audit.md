---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# Controllo, registrazione e monitoraggio
{: #aud-log-mon}

## Controllo
{: #auditing}

Puoi creare una politica di controllo del database che ti fornisce la possibilità di controllare varie categorie di eventi archiviate nelle tabelle degli eventi di controllo nel tuo database. Per ulteriori informazioni, vedi [Audit policy guidelines](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:external}.

Puoi inoltre controllare e tenere traccia delle modifiche al tuo database utilizzando i seguenti metodi:
* Creando un monitoraggio dell'evento `CHANGE HISTORY`, puoi eseguire la query della tabella di monitoraggio dell'evento per determinare cosa è stato fatto nel database e da chi. Per ulteriori informazioni, vedi [Monitoraggio eventi `CHANGE HISTORY`](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:external}.
* La Time Travel Query rende semplice archiviare tutte le modifiche ai tuoi dati e persino eseguire la query dei tuoi vecchi dati in base a un punto temporale selezionato. Per utilizzare questo metodo di verifica, assicurarti di aver prima impostato le tue tabelle per supportare Time Travel Query. Per ulteriori informazioni, vedi [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:external}

Per ulteriori informazioni sul controllo e sulla traccia delle modifiche al database, vedi [How do I audit or track changes?](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:external}.

## Registrazione e monitoraggio
{: #log_mon}

Il monitoraggio e la registrazione fanno parte del servizio, tuttavia, non vengono esposti direttamente all'utente finale. Viene invece utilizzata l'infrastruttura dallo staff operativo IBM per risolvere i problemi.  

Per la disponibilità del programma di traccia dell'attività, consulta [roadmap](https://ibm.biz/db2oncloud-roadmap){:external}.

Puoi connetterti con un client riga di comando Db2, come CLPPlus, per accedere alle diagnostiche e alle informazioni dettagliate.

### Una panoramica di base:
{: #basic_overview}

Esistono 2 tipi base di controllo. I controlli di integrità/tempo di attività esterni e il monitoraggio basato sulla metrica. IBM monitora centinaia di metriche e le archivia cronologicamente. In base ai valori di queste metriche, vengono generati degli avvisi. Questi avvisi vengono inviati allo staff operativo IBM per avere la certezza che vengano visti e risolti. Inoltre, IBM invia anche i log di diagnostica e di sistema operativo archiviati per una diagnosi rapida. {{site.data.keyword.Db2_on_Cloud_short}} è conforme al GDPR e le opzioni cloud dell'UE di IBM forniscono un elevato livello di conformità al GDPR, se necessario.


