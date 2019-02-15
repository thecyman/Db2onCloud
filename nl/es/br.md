---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-02"

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

# Copia de seguridad y restauración
{: #br}

Para los planes de pago, se realizan copias de seguridad cifradas de la base de datos a diario. Se conserva una copia de seguridad diaria para cada uno de los últimos 14 días.
{: shortdesc}

Además de las copias de seguridad estándar, puede utilizar [Time Travel Query ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} para conservar datos históricos para sus propios fines. También puede realizar sus propias exportaciones mediante IBM Data Studio o cualquier herramienta de Db2.
 
Para obtener información sobre restauraciones en un punto en el tiempo, consulte [Restauración en un punto en el tiempo](#point-in-time).

Normalmente, todos los planes de pago hacen uso de IBM Cloud Object Storage (COS) para mantener las copias de seguridad externas en tres centros de datos distintos. Sin embargo, es posible que Sídney y ciertos centros de datos más pequeños no den soporte a la replicación externa con IBM COS en este momento. Consulte la [documentación de IBM COS](/docs/services/cloud-object-storage/basics/endpoints.html#select-regions-and-endpoints) de su región para determinar qué regiones dan soporte a la replicación externa.

<!-- Retained backups are used by IBM for system recovery purposes in the event of a disaster or system loss. Use the [Time Travel Query ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:new_window} to keep historical data for your own purposes. In addition, you can also perform your own exports using IBM Data Studio or any Db2 tool. -->

<!-- To store your backups offsite at a remote storage site, make a request to IBM Support. -->

También puede utilizar la [CLI de IBM Lift ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://lift.ng.bluemix.net/){:new_window} para importar datos a {{site.data.keyword.Db2_on_Cloud_short}}.

## Restauración de punto en el tiempo
{: #point-in-time}

{{site.data.keyword.Db2_on_Cloud_short}} ha añadido la capacidad de restaurar a un punto en el tiempo. Puede restaurar desde sus copias de seguridad a un punto exacto en el tiempo. A día de hoy, para la mayoría de clientes, tiene que solicitar soporte para activar esta característica. Consulte la siguiente planificación de despliegue.

A continuación se ofrece una lista de disponibilidad de la característica de restauración a punto en el tiempo:
- Centro de datos de Dallas: Disponible actualmente en sistemas de servidor único
- En el resto de casos, incluida Europa y los sistemas de alta disponibilidad en Dallas: Solicite la activación de la característica al soporte técnico. El despliegue total en todos los sistemas se completará el 28 de febrero de 2019.
- Sistema dedicado IBM Cloud (anteriormente conocido como Bluemix dedicado): Disponible solamente abriendo una incidencia de soporte.

Lo siguiente es un ejemplo seleccionado de capturas de pantalla de la interfaz de usuario de la consola web donde se ha iniciado la operación de restauración a un punto en el tiempo y se indica su progreso:

1. Seleccione la estrategia de restauración de **Punto en el tiempo** y seleccione un punto en el tiempo al que desea restaurar la base de datos. El proceso de restauración a un punto en el tiempo selecciona la copia de seguridad más cercana al punto en el tiempo que ha solicitado, de entre la agrupación de copias de seguridad retenidas que se han hecho durante los 14 días anteriores. 

   El proceso de restauración a un punto en el tiempo invalida cualquier copia de seguridad retenida anteriormente con fechas posteriores al punto en el tiempo seleccionado debido a la divergencia resultante en la línea de tiempo.
   {: note}

   ![Vista de la selección resaltada de la estrategia de restauración de punto en el tiempo](images/pit_restore_1.png)

2. Confirme que desea continuar con sus selecciones de restauración. Después de iniciar la operación de restauración, no podrá cambiar la solicitud.  
![Vista del diálogo de confirmación de restauración a un punto en el tiempo](images/pit_restore_2.png)

3. Se está inicializando el proceso de restauración.
![Vista de la inicialización de la restauración a un punto en el tiempo](images/pit_restore_3.png)

4. Restaurando la base de datos al punto en el tiempo seleccionado.
![Vista del progreso de la restauración a un punto en el tiempo](images/pit_restore_4.png)

5. Se está creando un nuevo punto de copia de seguridad. La base de datos restaurada a un punto en el tiempo está lista para ser utilizada.
![Vista de la creación del nuevo punto de copia de seguridad](images/pit_restore_5.png)

6. La operación de restauración se ha completado con éxito.
![Vista de la finalización satisfactoria de la operación de restauración](images/pit_restore_6.png)

