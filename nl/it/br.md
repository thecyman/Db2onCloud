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

# Backup e ripristino
{: #bnr}

Per i piani a pagamento, i backup crittografati del database vengono eseguiti giornalmente. Un backup giornaliero viene conservato per ognuno degli ultimi 14 giorni.
{: shortdesc}

In aggiunta ai backup standard, puoi utilizzare [Time Travel Query ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} per conservare i dati cronologici per altri scopi, come ad esempio una query istantanea di dati precedenti o un controllo semplificato. Puoi anche eseguire le tue esportazioni utilizzando IBM Data Studio o un qualsiasi strumento Db2.
 
Per informazioni sui ripristini del punto temporale, consulta [Ripristino del punto temporale](#point-in-time).

Tutti i piani a pagamento normalmente utilizzano IBM Cloud Object Storage (COS) per conservare i backup offsite in 3 diversi data center. Tuttavia, Sydney e alcuni data center più piccoli potrebbero non supportare la replica offsite con IBM COS in questo momento. Consulta la [Documentazione IBM COS](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-endpoints#endpoints) per la tua regione per determinare quali regioni supportano la replica offsite.

Puoi anche utilizzare l'[IBM Lift CLI ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.lift-cli.cloud.ibm.com/){:new_window} per importare i dati in {{site.data.keyword.Db2_on_Cloud_short}}.

## Ripristino del punto temporale
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} ha aggiunto una funzionalità di ripristino del punto temporale. Puoi eseguire il ripristino in un punto nel tempo esatto dai tuoi backup. Oggi, per la maggior parte dei clienti, devi richiedere del supporto per attivare questa funzione. Consulta la seguente pianificazione di distribuzione.

Il seguente è un elenco di disponibilità della funzione di ripristino del punto temporale:
- Data center di Dallas: oggi disponibile su sistemi server singoli
- Tutti gli altri casi, inclusi i sistemi HA in Dallas e l'Europa: richiedi l'attivazione della funzione dal supporto. La distribuzione completa a tutti i sistemi sarà completata per il 28 febbraio 2019.
- Sistema IBM Cloud Dedicated: disponibile solo aprendo un ticket di supporto.

Di seguito viene riportato un esempio selezionato di acquisizioni schermo dell'IU della console web in cui l'operazione di ripristino del punto temporale è avviata e ne viene indicato l'avanzamento:

1. Seleziona la strategia di ripristino **Point in Time** e seleziona un data del punto temporale in cui vuoi ripristinare il database. Il processo di ripristino del punto temporale seleziona il backup più vicino alla tua data di punto temporale richiesta al di fuori del pool di backup conservati effettuati durante i precedenti 14 giorni. 

   Il processo di ripristino del punto temporale annulla la validità di tutti i backup conservati precedentemente con delle date successive alla data del punto temporale selezionata a causa di una divergenza risultante nella sequenza temporale.
   {: note}

   ![Vista della selezione evidenziata della strategia di ripristino del punto temporale](images/pit_restore_1.png)

2. Conferma di voler continuare con le tue selezioni di ripristino. Dopo aver avviato l'operazione di ripristino, non puoi modificare la richiesta.  
![Vista della finestra di dialogo della conferma del ripristino del punto temporale](images/pit_restore_2.png)

3. Il processo di ripristino viene inizializzato.
![Vista dell'inizializzazione del ripristino del punto temporale](images/pit_restore_3.png)

4. Ripristino del database al punto temporale selezionato.
![Vista dell'avanzamento del ripristino del punto temporale](images/pit_restore_4.png)

5. Stai creando un nuovo punto di backup. Il database ripristinato al punto temporale è pronto per l'utilizzo.
![Vista della creazione di un nuovo punto di backup](images/pit_restore_5.png)

6. L'operazione di ripristino è terminata correttamente.
![Vista del corretto completamento dell'operazione di ripristino](images/pit_restore_6.png)

