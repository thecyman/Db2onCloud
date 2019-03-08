---

copyright:
  years: 2014, 2019
lastupdated: "2018-10-22"

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

# Elevata disponibilità (HA)
{: #ha}

I piani di elevata disponibilità di {{site.data.keyword.Db2_on_Cloud_short}} dispongono di eccellenti caratteristiche disponibili con un 99.99% di SLA. 
{: shortdesc}

I piani di alta disponibilità standard senza un nodo di ripristino di emergenza (DR) forniscono gli aggiornamenti in sequenza e dell'errore senza problemi. Vengono gestiti per te tramite ACR (automatic client reroute) e gli IP portatili.

In aggiunta, puoi aggiungere un nodo di ripristino di emergenza (DR) con replica geografica. Questa opzione del nodo DR offsite ti fornisce la capacità di sincronizzare rapidamente i tuoi dati in tempo reale in un nodo del database in un data center {{site.data.keyword.Bluemix_notm}} di tua scelta. 

[Elenco delle ubicazioni dei data center in cui sono disponibili i nodi DR. ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} utilizza la tecnologia Db2 High Availability Disaster Recovery (HADR) in modalità `ASYNC` per raggiungere la capacità del nodo DR offsite e fornisce `Read on Standby` nel nodo DR.

## **Brasile: regola supplementare 14** (si applica ai sistemi forniti al governo federale brasiliano)
{: #rule_14}

In questo momento l'opzione di ripristino di emergenza (DR) per l'offerta Db2 on Cloud non è disponibile in Brasile per il governo federale a causa della regola supplementare 14.

## Come aggiungere un nodo di ripristino di emergenza (DR) con replica geografica
{: #add_dr}

Per gli utenti {{site.data.keyword.Db2_on_Cloud_short}} esistenti:
 * Puoi aggiungere un nodo DR su richiesta alle istanze {{site.data.keyword.Db2_on_Cloud_short}} esistenti. Dopo aver fatto clic sulla tua istanza nel dashboard {{site.data.keyword.Bluemix_notm}}, visualizzerai un'opzione denominata **Manage Disaster Recovery**. Puoi aggiungere un nodo di ripristino di emergenza (DR) con replica geografica da qui.
 * Se hai acquistato {{site.data.keyword.Db2_on_Cloud_short}} con contratto tramite una rappresentante delle vendite e non hai una sottoscrizione {{site.data.keyword.Bluemix_notm}}, contatta il tuo rappresentante di IBM per aggiungere un nodo DR.

Se al momento non sei un utente {{site.data.keyword.Db2_on_Cloud_short}}:
 * Ordina {{site.data.keyword.Db2_on_Cloud_short}} tramite {{site.data.keyword.Bluemix_notm}} o parla con il tuo rappresentante delle vendite.
 * Puoi quindi aggiungere un nodo DR utilizzando **Manage Disaster Recovery** nella console.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## Gestione dei nodi di ripristino di emergenza (DR) e di alta disponibilità (HA)
{: #manage_ha_dr}

Per i nodi HA standard, che non sono offsite, il failover viene gestito per te da IBM. IBM monitora l'integrità del tuo server, il failover e il failback se necessario, inclusi gli aggiornamenti continui e il ridimensionamento per mantenere il tempo di attività il più elevato possibile.

Per il ripristino di emergenza (DR) con replica geografica (HADR), devi eseguire il failover manualmente utilizzando **Manage Disaster Recovery** nella console. In aggiunta, puoi eseguire il failover utilizzando un'API come descritto [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}.

## Domande frequenti (FAQ)
{: #faq}

### Quali sono le modifiche necessarie per un'applicazione che utilizza Db2 per utilizzare il nodo di ripristino di emergenza DR dopo una sostituzione? Il nome DNS o l'indirizzo IP vengono modificati dopo la sostituzione?

**A**: no. Ti vengono forniti 2 nomi host risolvibili. Se la tua applicazione è configurata per utilizzare Db2 ACR (Active Connection Reroute), viene reinstradata al nuovo nodo primario.

Per ulteriori informazioni sul nodo di ripristino di emergenza (DR) con replica geografica, fai clic [qui ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}.
