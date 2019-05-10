---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-05"

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

# Funzioni e specifiche
{: #fs}

Le funzioni e le specifiche di {{site.data.keyword.Db2_on_Cloud_long}} sono qui riepilogate per tua convenienza.
{: shortdesc}

| Categoria | Funzione | Supportata? | Commenti |
|----------|---------|------------|----------|
| Generale | Db2 AESE | S | Db2 v11.1.3.3 |
|  | Read on Standby | S | Solo il nodo DR offsite |
|  | Aggiornamenti scaglionati automatici | S | Con i piani HA |
|  | Opzioni ubicazione data center | S | [Locations ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-locations){:new_window}. Consulta anche: Deployment & scaling durations. |
|  | BLU in memoria | S | Il valore predefinito è riga, specifica `CREATE TABLE..AS COL` per BLU |
|  | Programma di traccia dell'attività | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Accesso root fornito | N | Utilizza Ospitato Db2 se è obbligatorio l'accesso root |
|  |  |  |  |
| Alta disponibilità e replica | DR offsite | S | - |
|  | Alta disponibilità (2 nodi in 1 zona) | S | 99.99% SLA tempo di attività |
|  | Zone differenti nello stesso data center | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | **Nota**: l'HADR offsite è disponibile |
|  | Change Data Capture (CDC) | S | - |
|  | Utilizza come HADR da in loco | N | Utilizza CDC. Per informazioni, consulta [How can I migrate or sync data from Db2 to Db2 on Cloud? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Failover autonomo - HA | S | - |
|  | Failover autonomo - DR offsite | N | Utilizza il pulsante o l'API |
|  | Spostamenti IP con failover | S | Solo l'HA locale; non HADR offsite |
|  | RPO: Alta disponibilità | 0 s | L'HA è sincrona |
|  | RTO: Alta disponibilità | Normalmente 0-10 min | Con il codice di ripetizione, sarà visualizzato come lentezza con Db2 ACR |
|  | RPO: HADR nodo offsite | Normalmente < 15 s | Il DR offsite è asincrono |
|  | RTO: HADR nodo offsite | < 3 min | Deve essere avviato con il pulsante della console o l'API |
|  |  |  |  |
| Configurazioni di sistema | RAM e core massimi | 1 TB RAM, 48 core | Si applica al piano Precise Performance XL |
|  | Archiviazione massima | 11 TB | Si applica al piano Precise Performance XL. Disco per i dati e i log. |
|  | Flex: piano di base | 4 GB RAM, 1 core, disco da 2 GB | - |
|  | Flex: RAM e core massimi | 128 GB RAM, 32 core | Hai bisogno di specifiche più alte? Utilizza il piano Precise Performance o contatta il supporto IBM. |
|  | Flex: archiviazione massima | 4 TB | Disco per i dati e i log. Hai bisogno di specifiche più alte? Utilizza il piano Precise Performance o contatta il supporto IBM. |
|  |  |  |  |
| SLA e politiche di manutenzione | Piani di alta disponibilità | 99.99% | - |
|  | Piani server singolo | 99.5% | - |
|  | Nodo DR offsite | 99.5% | Devi utilizzare l'HA locale aggiuntiva per raggiungere il 99.99% |
|  | Politica di manutenzione | S | [Read details ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| Conformità di sicurezza | Pronto per HIPAA | S | Tutti i piani a pagamento incluso Flex. Devi richiedere la modalità HIPAA al supporto IBM. |
|  | HITRUST  | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | Oggi puoi utilizzare Ospitato Db2 per HITRUST |
|  | ISO (International Organization for Standardization)  | S | ISO 27001, 27002, 27017 e 27018 |
|  | Service Organization Controls (SOC) | S | SOC 2 Type 2 |
|  | GDPR | S | - |
|  | Cloud Europa | S | Utilizza la regione Francoforte. Supporto fornito fisicamente in Europa. |
|  | Elenco completo delle conformità | S | [Security compliances ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| Backup e ripristino | Backup giornalieri | S | 14 giorni di backup giornalieri |
|  | Ripristino self service in un momento specifico | Disponibile il 15 nov 2018 | [Ripristino del punto temporale](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
|  | Backup mantenuti offsite | Su richiesta | A partire dal primo dicembre 2018, offsite è il valore predefinito.  |
|  | Conservazione del backup fino a 10 anni | Su richiesta | A partire dal primo dicembre, 2018. Richiede il ticket di supporto. |
|  | Query dei vecchi dati senza ripristino | S | Devi configurare [Time Travel Query ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| Rete, sicurezza e VM | Macchina virtuale a singolo tenant | S | Tutti i piani a pagamento, incluso Flex, sono bare metal o VM a singolo tenant. |
|  | ICIAE | S | Richiedi al supporto IBM. Se stai richiedendo ICIAE per un ambiente esistente, i tuoi dati devono essere migrati al tuo ambiente ICIAE dal supporto IBM. |
|  | VPN | S | Richiedi al supporto IBM |
|  | Codifica sul disco | S | -  |
|  | Connessioni SSL/TLS | S | -  |
|  | Whitelist di IP | Alcuni | Disponibile al livello dell'utente Db2. Per il livello di rete, prendi in considerazione ICIAE o similari.  |
|  | Key Protect (Bring your own key) | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Servizio MIS / Interconnesso | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Limite massimo di connessioni simultanee: **Piano gratuito** | S | Massimo: 5 connessioni  |
|  | Limite massimo di connessioni simultanee: **Piani a pagamento** | N | Numero illimitato di connessioni  |
|  |  |  |  |
| Prezzi e acquisto | Sconti BYOL | S | [Announcement ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Disponibile su IBM Cloud | S | Sia Sottoscrizione che Pagamento a consumo |
|  | Disponibile con l'ordine della quota software | S | Tutti i piani incluso Flex. [Parts & details ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Disponibile su Hybrid Data Management Platform (HDMP) | S | Solo il piano Flex. [Dettagli su HDMP ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:new_window}|
|  | Fatturazione giornaliera | S | La fatturazione per i piani Flex si basa sul picco di utilizzo giornaliero. Ad esempio, se aumenti da 2 a 8 core un giorno per un'ora, sarai fatturato per 8 core solo per tale giorno e per 2 core per tutti gli altri giorni del mese. |
|  | Fatturazione oraria | [In roadmap ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | Metrica dei prezzi principale | Mensile | I prezzi sono indicati in termini mensili (ad esempio, $189 dollari al mese). Un prezzo mensile proporzionale si basa sul numero di giorni di servizio attivati durante il mese in cui il servizio è stato terminato. [Esempi](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
|  |  |  |  |
| Durate distribuzione e ridimensionamento | Dallas | **Distribuzione**: < 5 minuti. **Ridimensionamento**: < 45 minuti. | Solo il piano Flex, a seconda dell'inventario |
| | Altre regioni Stati Uniti Sud | **Distribuzione**: 1 giorno. **Ridimensionamento**: 8 ore. | Alcune ubicazioni più veloci di altre |
| | Francoforte e Londra | **Distribuzione**: < 5 min. **Ridimensionamento**: 2 ore. | Solo il piano Flex, a seconda dell'inventario |
| | Altre regioni Europa | **Distribuzione**: 3-5 giorni. **Ridimensionamento**: 1-2 giorni. | Alcune ubicazioni più veloci di altre |
| | Sydney | **Distribuzione**: < 1 ora. **Ridimensionamento**: 2 ore. | Solo il piano Flex, a seconda dell'inventario |
| | Altre regioni Asia Pacifico | **Distribuzione**: 3-5 giorni. **Ridimensionamento**: 3-5 giorni. | Alcune ubicazioni più veloci di altre. Minori volumi nelle regioni Asia Pacifico comportano tempi di provisioning dell'infrastruttura più lenti. |
{: caption="Tabella 1. Funzioni e specifiche supportate in Db2 on Cloud" caption-side="top"}

