---

copyright:
  years: 2014, 2018
lastupdated: "2018-11-01"

---

<!-- Attribute definitions --> 
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Características y especificaciones
{: #overview}

Aquí encontrará las características y especificaciones de {{site.data.keyword.Db2_on_Cloud_long}} resumidas para su comodidad.
{: shortdesc}

| Categoría | Característica | ¿Se admite? | Comentarios |
|----------|---------|------------|----------|
| General | AESE Db2 | Sí | Db2 v11.1.3.3 |
|  | Read on Standby | Sí | Solo nodo DR externo |
|  | Actualización continua automática | Sí | Con planes de alta disponibilidad |
|  | Opciones de ubicación de centro de datos | Sí | [Ubicaciones ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-locations){:new_window}. Vea también: Duraciones de despliegue y escalado. |
|  | BLU en memoria | Sí | El valor predeterminado es fila, especifique `CREATE TABLE..AS COL` para BLU |
|  | Activity Tracker | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Acceso raíz proporcionado | No | Utilice Db2 Hosted si es necesario el acceso raíz |
|  |  |  |  |
| Alta disponibilidad y replicación | DR externo | Sí | - |
|  | Alta disponibilidad (2 nodos en 1 zona) | Sí | SLA de tiempo de funcionamiento del 99,99% |
|  | Zonas diferentes en el mismo centro de datos | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | Change Data Capture (CDC) | Sí | - |
|  | Utilizar como HADR para local | No | Utilizar CDC. Para obtener información, consulte [¿Cómo puedo migrar o sincronizar los datos de Db2 a Db2 on Cloud? ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:new_window} |
|  | Migración tras error autónoma - Alta disponibilidad | Sí | - |
|  | Migración tras error autónoma - DR externo | No | Utilizar el botón o la API |
|  | La IP se mueve con la migración tras error | Sí | Solo alta disponibilidad local. Sin HADR externa |
|  |  |  |  |
| Políticas y SLA de mantenimiento | Planes de alta disponibilidad | 99,99% | - |
|  | Planes de servidor único | 99,5% | - |
|  | Nodo DR externo | 99,5% | Debe utilizar una alta disponibilidad local adicional para alcanzar el 99,99% |
|  | Política de mantenimiento | Sí | [Leer detalles ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:new_window} |
|  |  |  |  |
| Conformidad de seguridad | Preparada para HIPAA | Sí | Todos los planes de pago, incluido el flexible. Debe solicitar el modo HIPAA a IBM Support. <!--For Db2 Warehouse on Cloud [see docs here ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Db2whc/index.html#getting_started){:new_window}.--> |
|  | HITRUST  | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | Ahora Db2 Hosted puede utilizarse para HITRUST |
|  | International Organization for Standardization (organización internacional para la normalización, ISO)  | Sí | ISO 27001, 27002, 27017 y 27018 |
|  | Service Organization Controls (SOC) | Sí | SOC 2 de tipo 2 |
|  | GDPR | Sí | - |
|  | Nube de la UE | Sí | Utilice Frankfurt como región. Se proporciona soporte físico en la UE. |
|  | Lista completa de conformidades | Sí | [Conformidad de seguridad ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:new_window} |
|  |  |  |  |
| Copia de seguridad y restauración | Copias de seguridad diarias | Sí | 14 días de copia de seguridad diaria |
|  | Recuperación de autoservicio en un punto en el tiempo | Disponible el 15 de noviembre de 2018 | - |
|  | Copias de seguridad conservadas externamente | A petición | A fecha 1 de diciembre de 2018, el valor predeterminado es externo  |
|  | Conservar copias de seguridad hasta 10 años | A petición | A fecha 1 de diciembre de 2018. Requiere una incidencia de soporte. |
|  | Consultar datos antiguos sin restaurar | Sí | Debe configurar [Time Travel Query ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} |
|  |  |  |  |
| Red, seguridad y máquinas virtuales | Máquina virtual de un único arrendatario | Sí | Todos los planes de pago, incluido el flexible, son de máquina virtual de un único arrendatario o nativos. |
|  | ICIAE | Sí | Solicitud de IBM Support. Si se solicita ICIAE para un entorno de servicio existente, IBM Support debe mirar sus datos a su entorno ICIAE. |
|  | VPN | Sí | Solicitud de IBM Support |
|  | Cifrado en disco | Sí | -  |
|  | Conexiones SSL/TLS | Sí | -  |
|  | Elaboración de una lista blanca de IP | Algunos | Disponible a nivel de usuario de Db2. Para el nivel de red, considere ICIAE o similar.  |
|  | KeyProtect (Traiga su propia clave) | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  | MIS / Servicio interconectado | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - |
|  |  |  |  |
| Precios y compra | Descuentos BYOL | Sí | [Anuncio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-byol){:new_window} |
|  | Disponible a través de IBM Cloud | Sí | Tanto en suscripción como en pago según uso |
|  | Disponible a través de pedido de presupuesto de software | Sí | Todos los planes, incluido el flexible. [Partes y detalles. ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-parts-public){:new_window}|
|  | Facturación diaria | Sí | La facturación de los planes flexibles está basada en los picos de uso diario. Por ejemplo, si escala de 2 a 8 núcleos durante una hora de un día, se le facturarán 8 núcleos solo ese día y 2, el resto de los días del mes. |
|  | Facturación horaria | [En hoja de ruta ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.biz/db2oncloud-roadmap){:new_window} | - | 
|  | Métrica de precio principal | Mensual | Los precios se determinan mensualmente (por ejemplo, $189 USD al mes). El precio mensual prorrateado está basado en el número de días de servicio activado durante el mes en el que finaliza el servicio. [Ejemplos](plans_pricing.html) |
|  |  |  |  |
| Duraciones de despliegue y escalado | Dallas | **Despliegue**: < 5 minutos. **Escalado**: < 45 minutos. | Solo plan flexible, dependiendo del inventario |
| | EE.UU. Sur, otros | **Despliegue**: 1 día. **Escalado**: 8 horas. | Algunas ubicaciones son más cortas que otras |
| | Frankfurt y Londres | **Despliegue**: < 5 minutos. **Escalado**: 2 horas. | Solo plan flexible, dependiendo del inventario |
| | UE, otros | **Despliegue**: 3-5 días. **Escalado**: 1-2 días. | Algunas ubicaciones son más cortas que otras |
| | Sídney | **Despliegue**: < 1 hora. **Escalado**: 2 horas. | Solo plan flexible, dependiendo del inventario |
| | AP, otros | **Despliegue**: 3-5 días. **Escalado**: 3-5 días. | Algunas ubicaciones son más cortas que otras. Volúmenes menores en AP pueden causar tiempos de suministro de infraestructura más lentos. |
{: caption="Tabla 1. Características y especificaciones admitidas en Db2 on Cloud" caption-side="top"}

