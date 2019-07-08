---

copyright:
  years: 2014, 2019
lastupdated: "2019-04-08"

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

# Opciones de conectividad
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} ofrece diversas opciones de conectividad segura que dependen de los requisitos de conexión de la aplicación.  
{: shortdesc}

## Conexión a un punto final público (opción predeterminada)
{: #pub_endpt}

Al igual que sucede con cualquier servicio de nube público, puede conectar la aplicación mediante un nombre de host público que se proporciona en el momento en que se suministra el servicio. El acceso a los datos se protege mediante una autenticación fuerte, opciones de autorización de DB2 y controles de acceso, cifrado sobre cableado y sobre conexión en reposo y prácticas de conformidad y de seguridad de IBM para el desarrollo y para las operaciones. También se ofrece una lista blanca opcional de direcciones IP. Cree un caso de soporte de IBM si desea habilitar una lista blanca de direcciones IP.

### Cómo conectar con un punto final público:
{: #pub_endpt_steps}

La forma más sencilla de conectar los datos es mediante el nombre de host público que se proporciona en la carta de bienvenida. También puede obtener el nombre de host y las credenciales del siguiente modo:

1. Inicie una sesión en {{site.data.keyword.Db2_on_Cloud_short}} y pulse la instancia de servicio.
2. Pulse **Credenciales de servicio**.
3. Pulse **Nueva credencial** y luego pulse **Añadir**.
4. Una vez creadas las credenciales, bajo la columna `Acciones` pulse **Ver credenciales**.
5. En el siguiente ejemplo de documento JSON, anote el contenido de los campos de nombre de host, contraseña y nombre de usuario. Utilizará estos tres componentes para establecer una conexión de punto final público:

   ```
   {
     "hostname": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "password": "DTPY7KXxhp_pKtjLSt",
     "https_url": "https://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "port": 50000,
     "ssldsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxx.services.dal.bluemix.net;PORT=50001;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPY7KXWxhp_pKtjLSt;Security=SSL;",
     "host": "dashdb-enterprise-xxxxxxx.services.dal.bluemix.net",
     "jdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "uri": "db2://bluadmin:DTPY7KXx1p_pKtjLSt@dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50000/BLUDB",
     "db": "BLUDB",
     "dsn": "DATABASE=BLUDB;HOSTNAME=dashdb-enterprise-xxxxxxx.services.dal.bluemix.net;PORT=50000;PROTOCOL=TCPIP;UID=bluadmin;PWD=DTPYZunlWxhp_pKtjLSt;",
     "username": "bluadmin",
     "ssljdbcurl": "jdbc:db2://dashdb-enterprise-xxxxxxx.services.dal.bluemix.net:50001/BLUDB:sslConnection=true;"
   }

   ```

   ![Acceso de red pública a {{site.data.keyword.cloud_notm}}](images/public_connection.png "Vista gráfica de la conexión de usuario a nube")

## Conexión a un punto final privado: punto final de servicio de IBM Cloud
{: #priv_endpt}

Si tiene una aplicación desplegada en la cuenta de {{site.data.keyword.cloud_notm}} y desea conectarla a la base de datos sin que el tráfico de la base de datos fluya por redes públicas, puede utilizar la opción de **punto final de servicio de {{site.data.keyword.cloud_notm}}** cuando solicite la base de datos. Se le suministrará un nombre de host privado en el momento en que se suministre el servicio y solo puede conectarlo desde dentro de la cuenta de {{site.data.keyword.cloud_notm}}.  

Para obtener más información sobre la opción Punto final de servicio de {{site.data.keyword.cloud_notm}}, consulte [Punto final de servicio: acerca de](/docs/services/service-endpoint?topic=service-endpoint-about#about).


### Cómo conectar con un punto final privado con el punto final de servicio de IBM Cloud
{: #priv_endpt_steps}

La comunicación de red privada y de punto final se realiza mediante el servicio Punto final de servicio de {{site.data.keyword.cloud_notm}}. El Punto final de servicio facilita un tráfico de red rápido y seguro entre distintos servicios de {{site.data.keyword.cloud_notm}} y la base de datos del depósito a través de la placa posterior de red privada de {{site.data.keyword.cloud_notm}}. Este direccionamiento de red garantiza que los datos nunca pasan por internet pública. 

Para empezar a utilizar el punto final de servicio, la cuenta de {{site.data.keyword.cloud_notm}} debe estar habilitada para reenvío y direccionamiento virtual (VRF). Para habilitar la cuenta, consulte [Habilitación de la cuenta para que utilice el punto final de servicio mediante la CLI de IBM Cloud](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

Cuando la cuenta esté habilitada para VRF y el punto final de servicio esté habilitado, siga las instrucciones proporcionadas en la carta de bienvenida.

Ha llegado el momento de conectar la instancia de {{site.data.keyword.Db2_on_Cloud_short}} desde dentro de la cuenta de {{site.data.keyword.cloud_notm}} mediante el uso de la dirección de red privada proporcionada en la carta de bienvenida.

## Conexión a un punto final privado: red privada virtual (VPN)
{: #vpn}

Si tiene una aplicación desplegada en una red privada que está fuera de {{site.data.keyword.cloud_notm}} sin acceso a internet pública y desea conectarla a la base de datos sobre una conexión de red privada virtual (VPN), puede realizar la solicitud en el momento de solicitar el servicio o mediante la apertura de un caso de soporte de IBM. Los ingenieros de red de IBM ayudarán a sus ingenieros de red a configurar el túnel VPN entre su red privada e {{site.data.keyword.cloud_notm}}.

### Cómo conectar con un punto final privado con una VPN
{: #priv_endpt_vpn_steps}

Para establecer una conexión VPN con la base de datos en la nube detrás de un punto final público, [cree un caso de soporte de {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/unifiedsupport/cases/add){:external} que incluya los detalles siguientes:

* **Tipo de soporte**: Técnico 
* **Categoría**: Bases de datos 
* **Oferta**: seleccione su instancia de {{site.data.keyword.Db2_on_Cloud_short}} 
* **Asunto**: Solicitud de conexión VPN 
* **Descripción**: especifique la siguiente información necesaria
  * **Dirección de igual VPN del lado del cliente** (su punto final de VPN): `<IP Address>`
  * **Dominio de cifrado del lado del cliente** (sea específico – 10.0.0.0/8 no funciona porque el direccionamiento 10 también se utiliza dentro de {{site.data.keyword.cloud_notm}} para servicios de fondo): `<Domain>`
  * **Versión y hardware de VPN del lado del cliente**: `<Hardware and Version number>`
  * **Contacto de VPN del lado del cliente** (nombre y dirección de correo electrónico del contacto técnico): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Opcional** (cambie los valores únicamente si los valores predeterminados no resultan adecuados):

  *Parámetros de IKE/ISAKMP (Fase I)*

  * **Método de cifrado**: IKEv1
  * **Cifrado de IKE / Algoritmo de cifrado**: AES-256
  * **Algoritmo de autenticación**: SHA1
  * **Grupo de DH**: Grupo 5
  * **Tiempo de vida de asociación de seguridad (segundos)**: 1d (86400 segundos)

  *Parámetros de IPSEC (Fase II)*

  * **Cifrado de IPsec / Algoritmo de cifrado**: AES-256
  * **Algoritmo de autenticación**: SHA1
  * **Grupo de DH** (si se utiliza PF-Secrecy): Grupo 5
  * **Tiempo de vida de asociación de seguridad (segundos)**: 3600 segundos

Cuando reciban su solicitud, los técnicos de {{site.data.keyword.cloud_notm}} abrirán los puertos de cortafuegos adecuados y colocarán en la lista blanca la dirección IP proporcionada. La comunicación y la resolución de la solicitud se realizarán mediante una incidencia de caso de soporte de {{site.data.keyword.cloud_notm}}.

![Acceso de red pública a {{site.data.keyword.cloud_notm}} por medio de una VPN](images/public_connection_vpn.png "Vista gráfica de la conexión de usuario a nube")
