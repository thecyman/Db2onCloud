---

copyright:
  years: 2014, 2019
lastupdated: "2018-12-07"

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

# Plan gratuito
{: #free_plan}

El plan gratuito de {{site.data.keyword.Db2_on_Cloud_long}} proporciona los recursos básicos que le permiten desarrollar y aprender sobre Db2 sin ningún cargo.
{: shortdesc}

El plan gratuito no tiene límite de tiempo, pero los usuarios deben prolongar su plan gratuito cada 30 días.

Solo está disponible el soporte para la comunidad. 
 
## Arquitectura
{: #architecture}

A diferencia de otros planes de {{site.data.keyword.Db2_on_Cloud_short}}, el plan gratuito de {{site.data.keyword.Db2_on_Cloud_short}} se ejecuta en un sistema multiarrendatario. Los planes Flex y Precise Performance se ejecutan en sus propias máquinas virtuales de un solo arrendatario o en sus servidores dedicados.
 
El plan gratuito le permite utilizar un esquema de base de datos.

Para obtener más información sobre el plan gratuito de {{site.data.keyword.Db2_on_Cloud_short}}, consulte las [Preguntas más frecuentes ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oc_free_plan_faq){:new_window}.

## Utilización del plan gratuito fuera de América del Norte continental
{: #outside_na}

Actualmente se puede acceder al plan gratuito sin tarjeta de crédito desde América del Norte continental. Fuera de América del Norte continental, los clientes deben añadir una tarjeta de crédito a su cuenta de IBM Cloud y luego seleccionar la región "EE.UU. sur - Dallas" para que el plan gratuito aparezca y se pueda seleccionar.

El plan gratuito siempre es gratuito, y no se efectuará ningún cargo a la tarjeta de crédito.

## Restricciones del plan gratuito
{: #fp_restrictions}

Se recomienda encarecidamente utilizar un plan de servicio de nivel de empresa en lugar de un plan de servicio gratuito para cargas de trabajo de misión crítica o sensibles al rendimiento. 
{: important}

A continuación se muestra una tabla de restricciones del plan gratuito de {{site.data.keyword.Db2_on_Cloud_short}}:

| Categoría | Elemento | Restricción | 
|----------|------|-------------|
| Recursos | Almacenamiento | 200 MB de almacenamiento por usuario |
|  | Conexiones | 5 conexiones por usuario |
|  | Rendimiento | Es posible que el rendimiento fluctúe debido a cargas de trabajo ejecutadas por otros usuarios del sistema multiarrendatario |
|  |  |
| Características y funciones | Federación | No soportada |
|  | Compatibilidad con Oracle | No soportada |
|  | Extensiones definidas por el usuario (UDF) | No soportadas en ningún plan de {{site.data.keyword.Db2_on_Cloud_short}}, incluido el plan gratuito |
|  | Gestión de usuarios | Al usuario no se le da autoridad administrativa |
|  | Control de acceso a filas y columnas (RCAC) | No soportado |
|  | IBM InfoSphere Data Replication para uso en la carga de datos | No soportado |
|  |  |
| Entorno de red | IBM Cloud Integrated Analytics | No soportado |
|  | IBM Cloud Dedicated | No soportado |
|  |  |
| Conformidad de seguridad | Health Insurance Portability and Accountability Act de 1996 (HIPAA) | No soportada. Consulte la descripción de servicio. |
|  | Reglamento General de Protección de Datos de la Unión Europea (GDPR) | No soportada. Consulte la descripción de servicio. |
|  |  |
| Gestión de cuentas | Reactivación | Se requiere la reactivación cada 30 días. Si no se reactiva, los servicios del plan gratuito se suprimen 60 días más tarde.  |
{: caption="Tabla 1. {{site.data.keyword.Db2_on_Cloud_short}} Restricciones del plan gratuito" caption-side="top"}


