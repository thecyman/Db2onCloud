---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Copia de seguridad y restauración
{: #bnr}

Para los planes de pago, se realizan copias de seguridad cifradas de la base de datos a diario. Se conserva una copia de seguridad diaria para cada uno de los últimos 14 días.
{: shortdesc}

Además de las copias de seguridad estándar, puede utilizar
[Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} para el mantenimiento de datos históricos por otros motivos, como la consulta instantánea de datos antiguos o para simplificar la auditoría. También puede realizar sus propias exportaciones mediante IBM Data Studio o cualquier herramienta de Db2.
 
Para obtener información sobre restauraciones en un punto en el tiempo, consulte [Restauración en un punto en el tiempo](#point-in-time).

Normalmente, todos los planes de pago hacen uso de IBM Cloud Object Storage (COS) para mantener las copias de seguridad externas en tres centros de datos distintos. Sin embargo, es posible que Sídney y ciertos centros de datos más pequeños no den soporte a la replicación externa con IBM COS en este momento. Consulte la [documentación de IBM COS](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-endpoints#endpoints) de su región para determinar qué regiones dan soporte a la replicación externa.

También puede utilizar la [CLI de IBM Lift](https://www.lift-cli.cloud.ibm.com/){:external} para importar datos en {{site.data.keyword.Db2_on_Cloud_short}}.

## Restauración de punto en el tiempo
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} ha añadido la capacidad de restaurar a un punto en el tiempo. Puede restaurar desde sus copias de seguridad a un punto exacto en el tiempo. A día de hoy, para la mayoría de clientes, tiene que solicitar soporte para activar esta característica. Consulte la siguiente planificación de despliegue.

A continuación se ofrece una lista de disponibilidad de la característica de restauración a punto en el tiempo:
- Centro de datos de Dallas: Disponible actualmente en sistemas de servidor único
- En el resto de casos, incluida Europa y los sistemas de alta disponibilidad en Dallas: Solicite la activación de la característica al soporte técnico. El despliegue total en todos los sistemas se completará el 28 de febrero de 2019.
- Sistema dedicado IBM Cloud: Disponible solamente abriendo una incidencia de soporte.

Lo siguiente es un ejemplo seleccionado de capturas de pantalla de la interfaz de usuario de la consola web donde se ha iniciado la operación de restauración a un punto en el tiempo y se indica su progreso:

1. Seleccione la estrategia de restauración de **Punto en el tiempo** y seleccione un punto en el tiempo al que desea restaurar la base de datos. El proceso de restauración a un punto en el tiempo selecciona la copia de seguridad más cercana al punto en el tiempo que ha solicitado, de entre la agrupación de copias de seguridad retenidas que se han hecho durante los 14 días anteriores. 

   El proceso de restauración a un punto en el tiempo invalida cualquier copia de seguridad retenida anteriormente con fechas posteriores al punto en el tiempo seleccionado debido a la divergencia resultante en la línea de tiempo.
   {: note}

   ![Ver la selección resaltada de la estrategia de restauración de punto en el tiempo](images/pit_restore_1.png "Página de la consola de copia de seguridad y restauración")

2. Confirme que desea continuar con sus selecciones de restauración. Después de iniciar la operación de restauración, no podrá cambiar la solicitud.  
![Ver el diálogo de confirmación de restauración en punto en el tiempo](images/pit_restore_2.png "Diálogo de confirmación")

3. El proceso de restauración se está inicializando.
![Ver la inicialización de restauración de punto en el tiempo](images/pit_restore_3.png "Inicialización de restauración de punto en el tiempo")

4. Restaurando la base de datos al punto en el tiempo seleccionado.
![Ver el progreso de la restauración a unpunto en el tiempo](images/pit_restore_4.png "Progreso de la restauración")

5. Se está creando un nuevo punto de copia de seguridad. La base de datos restaurada a un punto en el tiempo está lista para ser utilizada.
![Vista de la creación de un punto de copia de seguridad](images/pit_restore_5.png "Creación de un punto de copia de seguridad")

6. La operación de restauración se ha completado con éxito.
![Vista de la finalización correcta de la restauración](images/pit_restore_6.png "Se ha completado correctamente")

