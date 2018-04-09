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

# Backup e ripristino 
{: #br}

Per i piani a pagamento, i backup crittografati del database vengono eseguiti giornalmente. Un backup giornaliero viene conservato per ognuno degli ultimi 14 giorni.
{: shortdesc}

I backup conservati vengono utilizzati da IBM solo per scopi di ripristino del sistema nel caso di un'emergenza o un danno al sistema. Utilizza la [Time Travel Query ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} per conservare i dati cronologici per i tuoi propri scopi. In aggiunta, puoi anche eseguire le tue proprie esportazioni utilizzando IBM Data Studio o un qualsiasi strumento Db2.

Per archiviare i tuoi backup offsite, in un sito di archiviazione remota, effettua una richiesta al supporto di IBM.

Puoi anche utilizzare la [IBM Lift CLI](https://lift.ng.bluemix.net/){:new_window} per importare i dati in {{site.data.keyword.Db2_on_Cloud_short}}.
