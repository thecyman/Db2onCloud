---

copyright:
  years: 2014, 2019
lastupdated: "2019-01-21"

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

# Gestión de accesos e identidades (IAM) en IBM Cloud
{: #iam}

La Gestión de accesos e identidades (IAM) le permite autenticar usuarios de forma segura para servicios de plataforma y controlar el acceso a recursos coherentes en todas las plataformas de {{site.data.keyword.Bluemix_notm}}. Por ejemplo, con un solo inicio de sesión en {{site.data.keyword.Bluemix_notm}} con su IBMid, tiene acceso a cualquiera de sus consolas de servicio y sus aplicaciones sin tener que iniciar sesión en cada uno.
{: shortdesc}

## ¿Está IAM habilitado en su instancia?
{: #enabled}

Durante un periodo de tiempo, las instancias de base de datos gestionadas por {{site.data.keyword.Db2_on_Cloud_long}} en {{site.data.keyword.Bluemix_notm}} podrán utilizar IAM para el control de acceso. Para comprobar que IAM está habilitado en su instancia, ejecute la consulta siguiente:

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

Si el valor devuelto de **IAM_ENABLED** es 1, IAM está habilitado en su instancia.

## Características de IBM Cloud IAM
{: #features}

Las siguientes características de IAM están implementadas en el servicio gestionado de {{site.data.keyword.Db2_on_Cloud_short}} con dos tipos de identidades admitidas:

**IBMid**

El administrador de base de datos debe agregar a los usuarios con un IBMid a cada instancia de servicio de base de datos a través de la consola o la API REST antes de que estos puedan conectarse a una instancia de servicio de base de datos en particular. Como para los usuarios sin IBMid, debe introducirse un ID de usuario para la instancia de servicio de base de datos al mismo tiempo que se agrega el usuario IBMid. Este ID de usuario debe ser único en la instancia de servicio de base de datos. Este ID de usuario también es el ID de autorización (AUTH) en la base de datos. El administrador de la base de datos puede otorgar y revocar permisos en función del ID AUTH.

**ID de servicio**

Un ID de servicio identifica un servicio o una aplicación de forma similar a cómo un ID de usuario identifica un usuario. Los ID de servicio son aquellos que pueden utilizar las aplicaciones para autenticarse con un servicio de IBM Cloud. Un ID de servicio representa una entidad separada del IBMid. Por lo tanto, se pueden otorgar diferentes autoridades y permisos específicos al ID de servicio en la base de datos. Los ID de servicio no tienen contraseña. Se debe crear una clave de API para cada ID de servicio para conectarla con la instancia de servicio de base de datos. Para obtener más información sobre los ID de servicio, consulte: [Introducción a los ID de servicio y a las claves de API de IBM Cloud IAM ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}.

## Conexiones de cliente e inicios de sesión de usuario
{: #connect_user}

**Requisito previo**: Cliente Db2 V11.1 FP3 y posterior.

Se pueden utilizar los siguientes métodos para la autenticación de IAM:

**Señal de acceso**

La aplicación puede obtener una señal de acceso directamente desde el servicio de IAM a través de la API REST utilizando una clave de API. Para obtener más información, consulte: [Obtención de una señal de IBM Cloud IAM utilizando una clave de API ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}. La señal de acceso tiene un periodo de validez predeterminado de 60 minutos antes de caducar. Si la señal ha caducado, el servidor Db2 no permitirá que se establezca la conexión. No se comprueba la caducidad de la señal después de establecer la conexión. Como antes de la integración IAM, la conexión permanecerá activa hasta que la aplicación se desconecte o se finalice la conexión por otros motivos.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

Una señal de acceso identifica a un usuario de IBMid o a un ID de servicio en la base de datos. El servidor de base de datos verifica la validez de la señal de acceso antes de aceptarla. Este es el mejor método si la aplicación necesita conectarse a más de una instancia de servicio de base de datos u otras instancias de servicio de {{site.data.keyword.Bluemix_notm}}, ya que minimiza la comunicación con el servicio de IAM para validar las señales de acceso.

**Clave de API**

Se pueden crear varias claves de API para cada usuario de IBMid o ID de servicio. Normalmente, se crea una clave de API para cada aplicación. Esto permite a la aplicación conectarse con la instancia de servicio de base de datos mientras el IBMid o el ID de servicio se añade como usuario a la misma instancia de servicio de base de datos. La clave de API tiene las mismas autoridades y permisos en la base de datos que el IBMid o el ID de servicio. Si desea que una aplicación no pueda volver a conectarse con la base de datos, puede eliminar la clave de API correspondiente. Este método de autenticación requiere menos cambios en la aplicación que utilizar una señal de acceso, ya que no requiere una interacción directa con el servicio de IAM. Para obtener más información sobre la creación y gestión de claves de API, consulte: [Gestión de claves de API de usuario ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}.

**IBMid/contraseña**

Se puede utilizar el IBMid/contraseña para iniciar sesión en la consola y también puede utilizarse en la aplicación del mismo modo que un ID de usuario/contraseña. La excepción sucede cuando el IBMid es federado ya que no se puede realizar una redirección a la página de inicio de su organización. Sin embargo, el método recomendado para que una aplicación establezca conexión con la instancia de servicio de base de datos es utilizar una señal de acceso.

## Interfaces soportadas
{: #sup-if}

Se admiten las siguientes interfaces de cliente de base de datos:

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC, CLP y CLPPLUS
{: #odbc-clpplus}

Para que una aplicación ODBC o un cliente de línea de mandatos (CLP, CLPPLUS) se conecte a un servidor de Db2 utilizando una autenticación IAM, primero debe configurarse un nombre de origen de datos (DSN) en el archivo de configuración `db2dsdriver.cfg` ejecutando el siguiente mandato:

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

El archivo de configuración `db2dsdriver.cfg` es un archivo XML ubicado normalmente en el directorio `sqllib/cfg`, que contiene una lista de alias de DSN y sus propiedades.

El siguiente ejemplo de archivo de configuración `db2dsdriver.cfg` muestra las configuraciones utilizadas para establecer una conexión con una instancia de servicio de base de datos. El archivo de configuración proporciona los alias de DSN, el nombre de la base de datos, el nombre del host (o dirección IP), el tipo de **Autenticación** y los valores del parámetro **SecurityTransportMode**:

```
<?xml version="1.0" encoding="UTF-8" standalone="no" ?>
<configuration>
        <dsncollection>
        <dsn alias="<data_source_name>" name="bludb" host="<host_name_or_IP_address>" port="50001">
            <parameter name="Authentication" value="GSSPLUGIN"/>
            <parameter name="SecurityTransportMode" value="SSL"/>
        </dsn>
        </dsncollection>
        <databases>
            <database name="bludb" host="<host_name_or_IP_address>" port="50001"/>
        </databases>
</configuration>
```

* La cadena de conexión ODBC puede contener uno de los siguientes:

    **Señal de acceso**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **Clave de API**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBMid/contraseña**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    Para ODBC, **AUTHENTICATION=GSSPLUGIN** puede especificarse en el archivo de configuración `db2dsdriver.cfg` o en la cadena de conexión de la aplicación.

* El mandato CONNECT de CLP puede contener una de las siguientes opciones:

    **Señal de acceso**

    Conectarse al servidor de base de datos `<database_server_name>` y pasar la señal de acceso ejecutando el mandato siguiente en el script o indicador de mandatos de CLP:

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **Clave de API**

    Conectarse al servidor de base de datos `<database_server_name>` con una clave de API ejecutando el mandato siguiente en el script o indicador de mandatos de CLP:

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBMid/contraseña**

    Conectarse al servidor de base de datos `<database_server_name>` con un IBMid y contraseña ejecutando el mandato siguiente en el script o indicador de mandatos CLP:

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    Para obtener información más detallada acerca de cómo conectarse a un servidor de base de datos con CLP, consulte: [Sentencia CONNECT (tipo 2) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}. 

* El mandato CONNECT de CLPPLUS puede contener una de las siguientes opciones:

    **Señal de acceso**

    Conéctese al alias de DSN (`@<data_source_name>`) y pase la señal de acceso ejecutando el siguiente mandato en el indicador de mandatos o script de CLPPLUS:

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **Clave de API**

    Conéctese al alias de DSN (`@<data_source_name>`) con una clave de API ejecutando el siguiente mandato en el indicador de mandatos o script de CLPPLUS:

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBMid/contraseña**

    Conéctese al alias de DSN (`@<data_source_name>`) con IBMid/contraseña ejecutando el siguiente mandato en el indicador de mandatos o script de CLPPLUS:

    `connect <IBMid>/<password>@<data_source_name>`

    Para obtener más información sobre como conectar alias DSN con CLPPLUS, consulte: [Alias de DSN en CLPPlus ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}.

### JDBC
{: #jdbc}

El tipo de controlador JDBC 4 está admitido para la autenticación de IAM.

Los ejemplos siguientes muestran fragmentos de código de conexión para los tres métodos:

**Señal de acceso**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setAccessToken( "<access_token>" );
Connection conn = dataSource.getConnection( );
```

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<nombre_host_o_dirección_IP>:50001/BLUDB:accessToken=<señal_acceso>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**Clave de API**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
dataSource.setApiKey( "<api_key>" );
Connection conn = dataSource.getConnection( );
```

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<nombre_host_o_dirección_IP>:50001/BLUDB:apikey=<clave_API>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBMid/contraseña**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<nombre_host_o_dirección_IP>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<IBMid>", "<contraseña>" );
```

o

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<nombre_host_o_dirección_IP>:50001/BLUDB:user=<IBMid>;password=<contraseña>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## Experiencia del usuario de consola
{: #console-ux}

La página de inicio de la consola de servicio tiene la opción de iniciar sesión con su IBMid y contraseña. Después de pulsar el botón **Iniciar sesión mediante IBMid** se dirige al usuario a la página de inicio de sesión de IAM, donde se introduce la contraseña. Cuando finaliza la autenticación, se vuelve a redirigir al usuario a la consola. Antes de que el inicio de sesión sea correcto, el administrador de la base de datos debe añadir al usuario de IBMid a cada instancia de servicio de base de datos a través de la consola o la API REST. Como para los usuarios sin IBMid, debe introducirse un ID de usuario para la instancia de servicio de base de datos al mismo tiempo que se agrega el usuario IBMid. El ID de usuario debe ser único en la instancia de servicio de base de datos. Este ID de usuario también es el ID de autorización (AUTH) en la base de datos.

## Experiencia de API REST
{: #api}

La API REST de {{site.data.keyword.Db2_on_Cloud_short}} se ha mejorado para admitir también una señal de acceso de IAM para las funciones que han aceptado previamente una señal de acceso generada por servicio de base de datos.

* Para añadir un nuevo usuario de IBMid, ejecute la siguiente llamada de API de ejemplo:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  El `<userid>` para `"id"` y `"ibmid"` no debe ser el mismo. Los dos ID no están enlazados de ninguna manera.
  {: note}

* Para migrar un usuario de base de datos que no sea IBMid (por ejemplo, `abcuser`) y hacer que sea un usuario IBMid, suprima primero el ID de usuario que no sea IBMid ejecutando la siguiente llamada API de ejemplo:

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  A continuación, vuelva a añadir el usuario con IBMid, que es el mismo ID de usuario que antes(`abcuser`), ejecutando la siguiente llamada de API de ejemplo:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Como el ID de usuario (`abcuser`) sigue siendo el mismo para el nuevo usuario IBMid para ese usuario, los permisos de base de datos otorgados al usuario siguen siendo los mismos. Si desea migrar una lista de usuarios de base de datos que no sean IBMid para convertirlos en usuarios IBMid, debe ejecutar las dos llamadas de API anteriores para cada usuario.

* Para añadir muchos usuarios IBMid nuevos de una vez, cree un archivo por lotes que liste las siguientes llamadas de API de ejemplo, una para cada usuario:

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

Para obtener más información sobre su API de servicio, consulte: [API REST de {{site.data.keyword.Db2_on_Cloud_short}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://ibm.biz/db2oc_api){:new_window}.

## Federación de IBMid
{: #fed_ibmid}

Para utilizar su propio proveedor de identidades como LDAP, primero debe federar su servidor LDAP con IBMid. Para obtener información sobre cómo federar su servidor LDAP con IBMid, consulte: [Guía de adopción de federación empresarial de IBMid ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}. Una vez la federación de IBMid haya finalizado y el administrador de la base de datos haya añadido a los usuarios permitidos en la instancia de servicio de base de datos, estos usuarios podrán iniciar sesión en la consola con su ID de usuario de la empresa y contraseña. Como alternativa, estos usuarios pueden utilizar una señal de acceso o clave de API que represente su ID de usuario para conectar con la instancia de servicio de base de datos a través de una de las interfaces de cliente de base de datos admitidas.

## Restricciones
{: #restrictions}

Existen las siguientes restricciones respecto a la autenticación IAM:

* La autenticación IAM para un cliente Db2 que se conecta a un servidor de Db2 solo está soportada sobre una conexión SSL.
* La federación IBMid está soportada para permitir el uso del portal de gestión de usuarios personalizados o el servidor para la autenticación. Este soporte no incluye la federación de grupos.
* La autenticación IAM para la federación de base de datos no está soportada.
* No está soportada la ejecución de mandatos IDA y extensiones definidas por el usuario (UDX) a través de CLPPlus.
* No está soportado el tipo de controlador JDBC 2.




