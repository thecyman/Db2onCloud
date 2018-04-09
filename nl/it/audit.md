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

# Controllo
{: #audit}

I seguenti sono i metodi con cui puoi controllare l'attività sul database {{site.data.keyword.Db2_on_Cloud_short}}:

* [CHANGE HISTORY event monitor ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

Creando un CHANGE HISTORY event monitor, puoi eseguire la query della tabella di monitoraggio dell'evento per determinare cosa è stato fatto nel database e da chi. 

La Time Travel Query rende semplice archiviare tutte le modifiche ai tuoi dati e persino eseguire la query dei tuoi vecchi dati in base a un punto temporale selezionato. Per utilizzare questo metodo di verifica, assicurarti di aver prima impostato le tue tabelle per supportare Time Travel Query. 

Per ulteriori informazioni su questi metodi di controllo, vedi [How do I audit or track changes? ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.
