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

# Alta disponibilidad (HA)
{: #ha}

Los planes de alta disponibilidad de {{site.data.keyword.Db2_on_Cloud_short}} ofrecen excelentes características de disponibilidad con un SLA del 99,99 %. 
{: shortdesc}

Los planes de alta disponibilidad estándar <!-- without a DR node -->proporcionan funciones de migración tras error ininterrumpida y de actualización continua. Se gestionan automáticamente mediante una redirección automática de cliente (ACR) e IP portables.

La función de alta disponibilidad con un nodo externo de recuperación tras desastre está actualmente en fase beta cerrada. Póngase en contacto con el representante de IBM para obtener información sobre cómo participar en la beta cerrada. El nodo DR externo le ofrece la posibilidad de sincronizar rápidamente sus datos en tiempo real con un nodo de base de datos en la ubicación externa que elija. {{site.data.keyword.Db2_on_Cloud_short}} utiliza la tecnología de recuperación tras desastre de alta disponibilidad de Db2 (HADR) en modalidad ASYNC para lograr la capacidad de nodo DR externo y ofrece la función Read on Standy en el nodo de recuperación tras desastre.
<!--- Through the web console, you can also add a disaster recovery (DR) node located in a datacenter of your choice. -->
