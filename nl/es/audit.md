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

# Auditoría
{: #audit}

A continuación se muestran los métodos con los que puede auditar la actividad de la base de datos {{site.data.keyword.Db2_on_Cloud_short}}:

* [Supervisor de sucesos del HISTORIAL DE CAMBIOS ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}
* [Time Travel Query ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}
{: shortdesc}

Mediante la creación de un supervisor de sucesos del HISTORIAL DE CAMBIOS, puede consultar la tabla del supervisor de sucesos para determinar lo que se ha hecho dentro de la base de datos y quién lo ha hecho. 

Time Travel Query facilita la tarea de almacenar todos los cambios en los datos y de consultar los datos antiguos en función de un punto en el tiempo seleccionado. Para utilizar este método de auditoría, asegúrese de configurar primero las tablas para que den soporte a Time Travel Query.

Para obtener más información sobre estos métodos de auditoría, consulte [Cómo puedo auditar y efectuar un seguimiento de los cambios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.
