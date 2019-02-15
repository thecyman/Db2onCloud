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

# Auditoría, registro y supervisión
{: #aud-log-mon}

## Auditoría
{: #auditing}

Puede crear una política de auditoría de base de datos que le dé la capacidad de auditar diferentes categorías de sucesos almacenados en las tablas de auditoría de sucesos de la base de datos. Para obtener más información, consulte [Directrices de políticas de auditoría ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html){:new_window}.

También puede auditar y realizar el seguimiento de cambios a la base de datos utilizando los métodos siguientes:
* Mediante la creación de un supervisor de sucesos de `CHANGE HISTORY`, puede consultar la tabla del supervisor de sucesos para determinar lo que se ha hecho dentro de la base de datos y quién lo ha hecho. Para obtener más información, consulte [Supervisor de sucesos `CHANGE HISTORY` ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){:new_window}.
* Time Travel Query facilita la tarea de almacenar todos los cambios en los datos y de consultar los datos antiguos en función de un punto en el tiempo seleccionado. Para utilizar este método de auditoría, asegúrese de configurar primero las tablas para que den soporte a Time Travel Query. Para obtener más información, consulte [Consulta de viaje en el tiempo ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl/){:new_window}

Para obtener más información sobre auditar y rastrear cambios en la base de datos, consulte [Cómo puedo auditar y efectuar un seguimiento de los cambios ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/427780/how-can-i-audit-or-track-changes-dropped-tables-to.html){:new_window}.

## Registro y supervisión
{: #log_mon}

La supervisión y el registro son parte del servicio; sin embargo, no están expuestos directamente al usuario final. En lugar de eso, el personal operativo de IBM utiliza la infraestructura para resolver problemas.  

Para consultar la disponibilidad del Rastreador de disponibilidad, consulte la [hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window}.

Puede conectarse mediante un cliente de línea de mandatos de Db2, como CLPPlus, para acceder a información detallada y diagnósticos.

### Una visión general básica:
{: #overview}

Hay 2 tipos de comprobación. Las comprobaciones de salud/tiempo de funcionamiento y las supervisiones basadas en métricas. IBM supervisa cientos de métricas y las almacena históricamente. Basándose en los valores de estas métricas, se generan alertas. Estas alertas se envían al personal de operaciones de IBM para asegurarse de que se ven y se responde a ellas. Además, IBM también envía registros del sistema operativo y de diagnóstico para una diagnosis rápida. {{site.data.keyword.Db2_on_Cloud_short}} cumple con el Reglamento general de protección de datos, y las opciones de IBM Cloud de IBM EU proporcionan un cumplimiento aún mayor de la normativa GDPR si es necesario.
