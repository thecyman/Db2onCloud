---

copyright:
  years: 2014, 2019
lastupdated: "2019-06-12"

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

# Funzioni e specifiche
{: #fs}

Le funzioni e le specifiche di {{site.data.keyword.Db2_on_Cloud_long}} sono qui riepilogate per tua convenienza.
{: shortdesc}


| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Db2 AESE | S | Db2 v11.1.3.3 |
| Read on Standby | S | Solo il nodo DR offsite |
| Aggiornamenti scaglionati automatici | S | Con i piani HA |
| Opzioni ubicazione data center | S | [Ubicazioni](https://ibm.biz/db2oncloud-locations){:external}. Consulta anche: Deployment & scaling durations. |
| BLU in memoria | S | Il valore predefinito è riga, specifica `CREATE TABLE..AS COL` per BLU |
| Programma di traccia dell'attività | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Accesso root fornito | N | Utilizza Ospitato Db2 se è obbligatorio l'accesso root |
{: class="simple-tab-table"}
{: caption="Tabella 1. Generale" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| DR offsite | S | - |
| Alta disponibilità (2 nodi in 1 zona) | S | 99.99% SLA tempo di attività |
| Zone differenti nello stesso data center | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | **Nota**: l'HADR offsite è disponibile |
| Change Data Capture (CDC) | S | - |
| Utilizza come HADR da in loco | N | Utilizza CDC. Per informazioni, vedi [How can I migrate or sync data from Db2 to Db2 on Cloud?](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external} |
| Failover autonomo - HA | S | - |
| Failover autonomo - DR offsite | N | Utilizza il pulsante o l'API |
| Spostamenti IP con failover | S | Solo l'HA locale; non HADR offsite |
| RPO: Alta disponibilità | 0 s | L'HA è sincrona |
| RTO: Alta disponibilità | Normalmente 0-10 min | Con il codice di ripetizione, sarà visualizzato come lentezza con Db2 ACR |
| RPO: HADR nodo offsite | Normalmente < 15 s | Il DR offsite è asincrono |
| RTO: HADR nodo offsite | < 3 min | Deve essere avviato con il pulsante della console o l'API |
{: class="simple-tab-table"}
{: caption="Tabella 2. Alta disponibilità e replica" caption-side="top"}
{: #simpletabtable2}
{: tab-title="High availability & replication"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| RAM e core massimi | 1 TB RAM, 48 core | Si applica al piano Precise Performance XL |
| Archiviazione massima | 11 TB | Si applica al piano Precise Performance XL. Disco per i dati e i log. |
| Flex: piano di base | 4 GB RAM, 1 core, disco da 2 GB | - |
| Flex: RAM e core massimi | 128 GB RAM, 32 core | Hai bisogno di specifiche più alte? Utilizza il piano Precise Performance o contatta il supporto IBM. |
| Flex: archiviazione massima | 4 TB | Disco per i dati e i log. Hai bisogno di specifiche più alte? Utilizza il piano Precise Performance o contatta il supporto IBM. |
{: class="simple-tab-table"}
{: caption="Tabella 3. Configurazioni di sistema" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Piani di alta disponibilità | 99.99% | - |
| Piani server singolo | 99.5% | - |
| Nodo DR offsite | 99.5% | Devi utilizzare l'HA locale aggiuntiva per raggiungere il 99.99% |
| Politica di manutenzione | S | [Leggi i dettagli](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabella 4. SLA e politiche di manutenzione " caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies & SLAs"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Pronto per HIPAA | S | Tutti i piani a pagamento incluso Flex. Devi richiedere la modalità HIPAA al supporto IBM. |
| HITRUST  | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | Oggi puoi utilizzare Ospitato Db2 per HITRUST |
| ISO (International Organization for Standardization)  | S | ISO 27001, 27002, 27017 e 27018 |
| Service Organization Controls (SOC) | S | SOC 2 Type 2 |
| GDPR | S | - |
| Cloud Europa | S | Utilizza la regione Francoforte. Supporto fornito fisicamente in Europa. |
| Elenco completo delle conformità | S | [Conformità di sicurezza](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabella 5. Conformità di sicurezza" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Backup giornalieri | S | 14 giorni di backup giornalieri |
| Ripristino self service in un momento specifico | Disponibile il 15 nov 2018 | [Ripristino del punto temporale](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| Backup mantenuti offsite | Su richiesta | A partire dal primo dicembre 2018, offsite è il valore predefinito.  |
| Conservazione del backup fino a 10 anni | Su richiesta | A partire dal primo dicembre, 2018. Richiede il ticket di supporto. |
| Query dei vecchi dati senza ripristino | S | Occorre configurare [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabella 6. Backup e ripristino" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup & restore"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Macchina virtuale a singolo tenant | S | Tutti i piani a pagamento, incluso Flex, sono bare metal o VM a singolo tenant. |
| ICIAE | S | Richiedi al supporto IBM. Se stai richiedendo ICIAE per un ambiente esistente, i tuoi dati devono essere migrati al tuo ambiente ICIAE dal supporto IBM. |
| VPN | S | Richiedi al supporto IBM |
| Codifica sul disco | S | -  |
| Connessioni SSL/TLS | S | -  |
| Whitelist di IP | Alcuni | Disponibile al livello dell'utente Db2. Per il livello di rete, prendi in considerazione ICIAE o similari.  |
| Key Protect (Bring your own key) | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Servizio MIS / Interconnesso | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Limite massimo di connessioni simultanee: **Piano gratuito** | S | Massimo: 5 connessioni  |
| Limite massimo di connessioni simultanee: **Piani a pagamento** | N | Numero illimitato di connessioni  |
{: class="simple-tab-table"}
{: caption="Tabella 7. Sicurezza di rete e VM" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, & VMs"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Sconti BYOL | S | [Annuncio](https://ibm.biz/db2oncloud-byol){:external} |
| Disponibile su IBM Cloud | S | Sia Sottoscrizione che Pagamento a consumo |
| Disponibile con l'ordine della quota software | S | Tutti i piani incluso Flex. [Parti e dettagli](https://ibm.biz/db2oncloud-parts-public){:external}|
| Disponibile su Hybrid Data Management Platform (HDMP) | S | Solo il piano Flex. [Dettagli relativi a HDMP](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| Fatturazione giornaliera | S | La fatturazione per i piani Flex si basa sul picco di utilizzo giornaliero. Ad esempio, se aumenti da 2 a 8 core un giorno per un'ora, sarai fatturato per 8 core solo per tale giorno e per 2 core per tutti gli altri giorni del mese. |
| Fatturazione oraria | [Nella roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
| Metrica dei prezzi principale | Mensile | I prezzi sono indicati in termini mensili (ad esempio, $189 dollari al mese). Un prezzo mensile proporzionale si basa sul numero di giorni di servizio attivati durante il mese in cui il servizio è stato terminato. [Esempi](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="Tabella 8. Prezzi e acquisto" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| Funzione | Supportata? | Commenti |
|---------|------------|----------|
| Dallas | **Distribuzione**: < 5 minuti. **Ridimensionamento**: < 45 minuti. | Solo il piano Flex, a seconda dell'inventario |
| Altre regioni Stati Uniti Sud | **Distribuzione**: 1 giorno. **Ridimensionamento**: 8 ore. | Alcune ubicazioni più veloci di altre |
| Francoforte e Londra | **Distribuzione**: < 5 min. **Ridimensionamento**: 2 ore. | Solo il piano Flex, a seconda dell'inventario |
| Altre regioni Europa | **Distribuzione**: 3-5 giorni. **Ridimensionamento**: 1-2 giorni. | Alcune ubicazioni più veloci di altre |
| Sydney | **Distribuzione**: < 1 ora. **Ridimensionamento**: 2 ore. | Solo il piano Flex, a seconda dell'inventario |
| Altre regioni Asia Pacifico | **Distribuzione**: 3-5 giorni. **Ridimensionamento**: 3-5 giorni. | Alcune ubicazioni più veloci di altre. Minori volumi nelle regioni Asia Pacifico comportano tempi di provisioning dell'infrastruttura più lenti. |
{: class="simple-tab-table"}
{: caption="Tabella 9. Durate distribuzione e ridimensionamento " caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment & scaling durations"}
{: tab-group="fs"}

