---

copyright:
  years: 2014, 2019
lastupdated: "2019-06-13"

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

# Características y especificaciones
{: #fs}

Aquí encontrará las características y especificaciones de {{site.data.keyword.Db2_on_Cloud_long}} resumidas para su comodidad.
{: shortdesc}


| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| AESE Db2 | Sí | Db2 v11.1.3.3 |
| Read on Standby | Sí | Solo nodo DR externo |
| Actualización continua automática | Sí | Con planes de alta disponibilidad |
| Opciones de ubicación de centro de datos | Sí | [Ubicaciones](https://ibm.biz/db2oncloud-locations){:external}. Vea también: Duraciones de despliegue y escalado. |
| BLU en memoria | Sí | El valor predeterminado es fila, especifique `CREATE TABLE..AS COL` para BLU |
| Activity Tracker | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Acceso raíz proporcionado | No | Utilice Db2 Hosted si es necesario el acceso raíz |
{: class="simple-tab-table"}
{: caption="Tabla 1. General" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| DR externo | Sí | - |
| Alta disponibilidad (2 nodos en 1 zona) | Sí | SLA de tiempo de funcionamiento del 99,99% |
| Zonas diferentes en el mismo centro de datos | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | **Nota**: Está disponible el HADR externo |
| Change Data Capture (CDC) | Sí | - |
| Utilizar como HADR para local | No | Utilizar CDC. Para obtener información, consulte [¿Cómo puedo migrar o sincronizar los datos de Db2 a Db2 on Cloud?](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external} |
| Migración tras error autónoma - Alta disponibilidad | Sí | - |
| Migración tras error autónoma - DR externo | No | Utilizar el botón o la API |
| La IP se mueve con la migración tras error | Sí | Solo alta disponibilidad local. Sin HADR externa |
| RPO: Alta disponibilidad | 0 s | HA es síncrona |
| RTO: Alta disponibilidad | Normalmente 0-10 min | Con código de reintento, aparecerá como lentitud con ACR de Db2 |
| RPO: Nodo HADR externo | Normalmente < 15 s | El DR externo es asíncrono |
| RTO: Nodo HADR externo | < 3 min | Debe iniciarse con botón de consola o API |
{: class="simple-tab-table"}
{: caption="Tabla 2. Alta disponibilidad y réplicas" caption-side="top"}
{: #simpletabtable2}
{: tab-title="High availability & replication"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| RAM y núcleos máximos | 1 TB RAM, 48 núcleos | Se aplica al plan Precise Performance XL |
| Almacenamiento máximo | 11 TB | Se aplica al plan Precise Performance XL. Mismo disco para datos y archivos de registro. |
| Flex: plan base | 4 GB RAM, 1 núcleo, 2 GB disco | - |
| Flex: Máximo RAM y núcleos | 128 GB RAM, 32 núcleos | ¿Necesita especificaciones más altas? Utilice Precise Performance plan o póngase en contacto con el soporte de IBM. |
| Flex: Almacenamiento máximo | 4 TB | Mismo disco para datos y archivos de registro. ¿Necesita especificaciones más altas? Utilice Precise Performance plan o póngase en contacto con el soporte de IBM. |
{: class="simple-tab-table"}
{: caption="Tabla 3. Configuraciones del sistema" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Planes de alta disponibilidad | 99,99% | - |
| Planes de servidor único | 99,5% | - |
| Nodo DR externo | 99,5% | Debe utilizar una alta disponibilidad local adicional para alcanzar el 99,99% |
| Política de mantenimiento | Sí | [Leer detalles](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabla 4. Políticas de mantenimiento y los SLA" caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies & SLAs"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Preparada para HIPAA | Sí | Todos los planes de pago, incluido el flexible. Debe solicitar el modo HIPAA al equipo de soporte de IBM. |
| HITRUST  | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | Ahora Db2 Hosted puede utilizarse para HITRUST |
| International Organization for Standardization (organización internacional para la normalización, ISO)  | Sí | ISO 27001, 27002, 27017 y 27018 |
| Service Organization Controls (SOC) | Sí | SOC 2 de tipo 2 |
| GDPR | Sí | - |
| Nube de la UE | Sí | Utilice Frankfurt como región. Se proporciona soporte físico en la UE. |
| Lista completa de conformidades | Sí | [Conformidad de seguridad](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabla 5. Conformidad de seguridad" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Copias de seguridad diarias | Sí | 14 días de copia de seguridad diaria |
| Recuperación de autoservicio en un punto en el tiempo | Disponible el 15 de noviembre de 2018 | [Restauración de punto en el tiempo](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| Copias de seguridad conservadas externamente | A petición | A fecha 1 de diciembre de 2018, el valor predeterminado es externo  |
| Conservar copias de seguridad hasta 10 años | A petición | A fecha 1 de diciembre de 2018. Requiere una incidencia de soporte. |
| Consultar datos antiguos sin restaurar | Sí | Debe configurar
[Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabla 6. Copia de seguridad y restauración" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup & restore"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Máquina virtual de un único arrendatario | Sí | Todos los planes de pago, incluido el flexible, son de máquina virtual de un único arrendatario o nativos. |
| ICIAE | Sí | Solicitud de IBM Support. Si se solicita ICIAE para un entorno de servicio existente, IBM Support debe migrar sus datos a su entorno ICIAE. |
| VPN | Sí | Solicitud de IBM Support |
| Cifrado en disco | Sí | -  |
| Conexiones SSL/TLS | Sí | -  |
| Elaboración de una lista blanca de IP | Algunos | Disponible a nivel de usuario de Db2. Para el nivel de red, considere ICIAE o similar.  |
| Key Protect (traiga su propia clave) | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| MIS / Servicio interconectado | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Límite de conexiones simultáneas máximas: **Plan gratuito** | Sí | Máximo: 5 conexiones  |
| Límite de conexiones simultáneas máximas: **Planes de pago** | No | Número de conexiones ilimitado  |
{: class="simple-tab-table"}
{: caption="Tabla 7. Red, seguridad y máquinas virtuales" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, & VMs"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Descuentos BYOL | Sí | [Aviso](https://ibm.biz/db2oncloud-byol){:external} |
| Disponible en IBM Cloud | Sí | Tanto en suscripción como en pago según uso |
| Disponible a través de pedido de presupuesto de software | Sí | Todos los planes, incluido el flexible. [Piezas y detalles](https://ibm.biz/db2oncloud-parts-public){:external}|
| Disponible en Plataforma de gestión de datos híbrida (HDMP) | Sí | Solo plan flexible. [Detalles sobre HDMP](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| Facturación diaria | Sí | La facturación de los planes flexibles está basada en los picos de uso diario. Por ejemplo, si escala de 2 a 8 núcleos durante una hora de un día, se le facturarán 8 núcleos solo ese día y 2, el resto de los días del mes. |
| Facturación horaria | [En hoja de ruta](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
| Métrica de precio principal | Mensual | Los precios se determinan mensualmente (por ejemplo, $189 USD al mes). El precio mensual prorrateado está basado en el número de días de servicio activado durante el mes en el que finaliza el servicio. [Ejemplos](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="Tabla 8. Precios y compra" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| Característica | ¿Se admite? | Comentarios |
|---------|------------|----------|
| Dallas | **Despliegue**: < 5 minutos. **Escalado**: < 45 minutos. | Solo plan flexible, dependiendo del inventario |
| EE.UU. sur, otros | **Despliegue**: 1 día. **Escalado**: 8 horas. | Algunas ubicaciones son más cortas que otras |
| Frankfurt y Londres | **Despliegue**: < 5 minutos **Escalado**: 2 horas. | Solo plan flexible, dependiendo del inventario |
| UE, otros | **Despliegue**: 3-5 días. **Escalado**: 1-2 días. | Algunas ubicaciones son más cortas que otras |
| Sídney | **Despliegue**: < 1 hora. **Escalado**: 2 horas. | Solo plan flexible, dependiendo del inventario |
| AP, otros | **Despliegue**: 3-5 días. **Escalado**: 3-5 días. | Algunas ubicaciones son más cortas que otras. Volúmenes menores en AP pueden causar tiempos de suministro de infraestructura más lentos. |
{: class="simple-tab-table"}
{: caption="Tabla 9. Despliegue y duración de escalada" caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment & scaling durations"}
{: tab-group="fs"}

