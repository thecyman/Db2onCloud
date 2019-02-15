---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-10"

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

# Controllo, registrazione e monitoraggio
{: #aud-log-mon}

## Controllo
{: #auditing}

Puoi creare una politica di controllo del database che ti fornisce la possibilità di controllare varie categorie di eventi archiviate nelle tabelle degli eventi di controllo nel tuo database. Per ulteriori informazioni, vedi [Audit policy guidelines ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}.

Puoi inoltre controllare e tenere traccia delle modifiche al tuo database utilizzando i seguenti metodi:
* Creando un monitoraggio dell'evento `CHANGE HISTORY`, puoi eseguire la query della tabella di monitoraggio dell'evento per determinare cosa è stato fatto nel database e da chi. Per ulteriori informazioni, vedi il [Monitoraggio dell'evento `CHANGE HISTORY` ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}.
* La Time Travel Query rende semplice archiviare tutte le modifiche ai tuoi dati e persino eseguire la query dei tuoi vecchi dati in base a un punto temporale selezionato. Per utilizzare questo metodo di verifica, assicurarti di aver prima impostato le tue tabelle per supportare Time Travel Query. Per ulteriori informazioni, vedi [Time Travel Query ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}

Per ulteriori informazioni sul controllo e la traccia delle modifiche al database, vedi [How do I audit or track changes? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Registrazione e monitoraggio
{: #log_mon}

Il monitoraggio e la registrazione fanno parte del servizio, tuttavia, non vengono esposti direttamente all'utente finale. Viene invece utilizzata l'infrastruttura dallo staff operativo IBM per risolvere i problemi.  

Per la disponibilità del programma di traccia dell'attività, consulta [roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window}.

Puoi connetterti con un client riga di comando Db2, come CLPPlus, per accedere alle diagnostiche e alle informazioni dettagliate.

### Una panoramica di base:
{: #overview}

Esistono 2 tipi base di controllo. I controlli di integrità/tempo di attività esterni e il monitoraggio basato sulla metrica. IBM monitora centinaia di metriche e le archivia cronologicamente. In base ai valori di queste metriche, vengono generati degli avvisi. Questi avvisi vengono inviati allo staff operativo IBM per avere la certezza che vengano visti e risolti. Inoltre, IBM invia anche i log di diagnostica e di sistema operativo archiviati per una diagnosi rapida. {{site.data.keyword.Db2_on_Cloud_short}} è conforme al GDPR e le opzioni cloud dell'UE di IBM forniscono un elevato livello di conformità al GDPR, se necessario.
