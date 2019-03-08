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

# Alta disponibilidad (HA)
{: #ha}

Los planes de alta disponibilidad de {{site.data.keyword.Db2_on_Cloud_short}} ofrecen excelentes características de disponibilidad con un SLA del 99,99 %. 
{: shortdesc}

Los planes de alta disponibilidad estándar sin nodo de recuperación tras desastre (DR) proporcionan funciones de migración tras error ininterrumpida y de actualización continua. Se gestionan automáticamente mediante una redirección automática de cliente (ACR) e IP portables.

Además, puede añadir un nodo de recuperación tras desastre replicado geográficamente. Esta opción de nodo DR externo le ofrece la posibilidad de sincronizar rápidamente sus datos en tiempo real con un nodo de base de datos en el centro de datos externo de {{site.data.keyword.Bluemix_notm}} que elija. 

[Lista de ubicaciones de centros de datos donde hay disponibles nodos de DR. ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/366888/what-locations-cities-or-countries-is-dashdb-avail.html){:new_window}

{{site.data.keyword.Db2_on_Cloud_short}} utiliza la tecnología de recuperación tras desastre de alta disponibilidad de Db2 (HADR) en modalidad `ASYNC` para lograr la capacidad de nodo DR externo y ofrece la función `Read on Standby` en el nodo DR.

## **Brasil: Norma suplementaria 14** (se aplica a los sistemas suministrados para el gobierno federal brasileño)
{: #rule_14}

En este momento, la opción de recuperación tras desastre (DR) para las ofertas de Db2 on Cloud no está disponible en Brasil para el gobierno federal debido a la Norma suplementaria 14.

## Cómo añadir un nodo de recuperación tras desastre replicado geográficamente
{: #add_dr}

Para usuarios actuales de {{site.data.keyword.Db2_on_Cloud_short}}:
 * Puede añadir un nodo DR bajo demanda a las instancias existentes de {{site.data.keyword.Db2_on_Cloud_short}}. Tras pulsar la instancia en el panel de control de {{site.data.keyword.Bluemix_notm}}, verá una opción denominada **Gestionar recuperación tras desastre**. Desde allí, puede añadir un nodo de recuperación tras desastre replicado geográficamente.
 * Si ha adquirido {{site.data.keyword.Db2_on_Cloud_short}} en contrato mediante un representante de ventas y no dispone de suscripción a {{site.data.keyword.Bluemix_notm}}, póngase en contacto con el representante de IBM para añadir un nodo DR.

Si actualmente no es usuario de {{site.data.keyword.Db2_on_Cloud_short}}:
 * Solicite {{site.data.keyword.Db2_on_Cloud_short}} mediante {{site.data.keyword.Bluemix_notm}} o póngase en contacto con un representante de ventas.
 * Puede añadir un nodo DR mediante la opción **Gestionar recuperación tras desastre** en la consola.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->

## Gestión de nodos de recuperación tras desastre y alta disponibilidad
{: #manage_ha_dr}

Para los nodos HA estándar, que no son externos, IBM gestiona la migración tras error por usted. IBM supervisa el estado del servidor, la migración tras error y la vuelta a utilizar el servidor de nuevo según sea necesario, incluidas las actualizaciones continuas y el escalado para mantener al máximo el tiempo de funcionamiento.

Para la recuperación tras desastre replicada geográficamente (HADR), debe realizar la migración tras error manualmente mediante **Gestionar recuperación tras desastre** en la consola. Además, puede realizar la migración tras error mediante una API, tal como se describe [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/457901/where-can-i-find-api-documentation-for-db2-on-clou.html){:new_window}.

## Preguntas más frecuentes
{: #faq}

### ¿Cuáles son los cambios necesarios para una aplicación que utiliza Db2 para trabajar con el nodo DR tras la toma de control? ¿Cambian el nombre DNS o la dirección IP tras la toma de control?

**R**: No. Se proporcionan 2 nombres de host que se pueden resolver. Si la app está configurada para utilizar Db2 ACR (Active Connection Reroute), la app se reencamina al nuevo nodo primario.

Para obtener más información sobre el nodo de recuperación tras desastre replicado geográficamente, pulse [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/458385/frequently-asked-questions-for-db2-on-cloud-hadr-g.html){:new_window}.
