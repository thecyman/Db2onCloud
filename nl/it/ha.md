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

# Elevata disponibilità (HA) 
{: #ha}

I piani di elevata disponibilità di {{site.data.keyword.Db2_on_Cloud_short}} dispongono di eccellenti caratteristiche disponibili con un 99.99% di SLA.
{: shortdesc}

I piani di elevata disponibilità standard <!-- without a DR node -->forniscono gli aggiornamenti in sequenza e dell'errore senza problemi. Vengono gestiti per te tramite ACR (automatic client reroute) e gli IP portatili.

L'elevata disponibilità con un nodo di ripristino di emergenza offsite è al momento nella beta chiusa. Contatta il tuo rappresentate IBM per avere informazioni sulla partecipazione alla beta chiusa. Il nodo DR offsite ti fornisce la capacità di sincronizzare rapidamente i tuoi dati in tempo reale in un nodo del database in un'ubicazione offsite di tua scelta. {{site.data.keyword.Db2_on_Cloud_short}} utilizza la tecnologia Db2 High Availability Disaster Recovery (HADR) in modalità ASINCRONA per raggiungere la capacità del nodo DR e fornisce Read on Standy nel nodo di ripristino di emergenza.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
