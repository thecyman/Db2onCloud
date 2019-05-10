---

copyright:
  years: 2014, 2019
lastupdated: "2018-05-11"

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

# Migración de datos a IBM Cloud
{: #migration}

Puede cargar datos desde un archivo de datos en un formato delimitado como (CSV o TXT) situado en una red local o en un almacén de objetos (Amazon S3 o IBM Cloud Object Storage) en {{site.data.keyword.Db2_on_Cloud_long}}. Incluso puede migrar datos desde un sistema local.
{: shortdesc}

## Carga de datos desde un almacén de objetos
{: #cos}

Para cargar datos desde Amazon S3, utilice uno de los siguientes métodos:
  * Consola web de {{site.data.keyword.Db2_on_Cloud_short}}. **Cargar > Amazon S3**. 
  * Tablas externas directamente. A continuación se muestra una sentencia SQL de ejemplo:

    ```
    INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
        (CCSID 1208 s3('s3.amazonaws.com',
        '<S3-access-key-ID>',
        '<S3-secret-access-key>',
        '<my_bucket>'
           )
      )      
    ```

Para cargar datos desde IBM Cloud Object Storage mediante tablas externas directamente, examine esta sentencia SQL de ejemplo:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3-api.us-geo.objectstorage.softlayer.net',
  '<S3-access-key-ID>',
  '<S3-secret-access-key>',
  '<my_bucket>'
     )
  )      
```

Para IBM Cloud Object Storage, para crear credenciales de HMAC al crear nuevas credenciales de servicio, especifique {"HMAC:true"} en el campo *Añadir parámetros de configuración en línea*.
{: note}

## Migración de datos desde un sistema local
{: #onprem}

Para migrar datos desde un sistema local, elija uno de los siguientes métodos, en función del tamaño del conjunto de datos:
* Menos de 25 TB de datos: [CLI de IBM Lift](#lift)
* 25 TB de datos o más: [Migración de datos masiva de IBM Cloud](#mdms)

### CLI de Lift
{: #lift}

La CLI de Lift es una aplicación que puede utilizar de forma gratuita para migrar datos a {{site.data.keyword.Bluemix_notm}} desde los distintos orígenes de datos que se muestran en la Tabla 1. 

| Base de datos de destino en IBM Cloud | Origen de datos |
|------------------------------|-------------|
| {{site.data.keyword.Db2_on_Cloud_long_notm}}   | IBM Db2 |
|                              | Base de datos Oracle |
|                              | Microsoft SQL Server |
|                              | Formato de archivo CSV |
{: caption="Tabla 1. Orígenes de datos de la migración" caption-side="top"}

Para descargar e instalar la CLI de Lift, consulte: [Descarga de la CLI de Lift ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.lift-cli.cloud.ibm.com/#download){:new_window}.

Para ver instrucciones paso a paso sobre cómo migrar los datos a {{site.data.keyword.Bluemix_notm}} mediante la CLI de Lift, consulte: [Migración de datos a {{site.data.keyword.Db2_on_Cloud_long_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.lift-cli.cloud.ibm.com/#docs){:new_window}.

### Migración de datos masiva de IBM Cloud
{: #mdms}

Un método rápido, sencillo y seguro de transferir físicamente terabytes o petabytes de datos a {{site.data.keyword.Bluemix_notm}}. La migración de datos masiva es un dispositivo de almacenamiento móvil con 120 TB de capacidad de almacenamiento utilizable para acelerar la transferencia de datos a {{site.data.keyword.Bluemix_notm}}. Con esta solución puede hacer frente a los retos comunes que plantean las transferencias, como el alto coste, los tiempos de transferencia largos y los problemas de seguridad, en un solo servicio.

![Vista del dispositivo de migración de datos masiva](images/mdms.svg)

Para obtener más información sobre el dispositivo de migración de datos masiva, consulte la [Guía de aprendizaje de iniciación](/docs/infrastructure/mass-data-migration?topic=mass-data-migration-getting-started-tutorial#getting-started-with-ibm-cloud-mass-data-migration){:new_window}.

