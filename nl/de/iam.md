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

# Identity and Access Management (IAM) in IBM Cloud
{: #iam}

Identity and Access Management (IAM) ermöglicht Ihnen die sichere Authentifizierung von Benutzern für Plattformservices und die konsistente Steuerung des Zugriffs auf Ressourcen in der gesamten {{site.data.keyword.Bluemix_notm}}-Plattform. So verfügen Sie beispielsweise mit nur einer einzigen Anmeldung bei {{site.data.keyword.Bluemix_notm}} mit Ihrer IBMid über Zugriff auf jede Ihrer Servicekonsolen und die zugehörigen Anwendungen, ohne dass Sie sich jedes Mal separat anmelden müssen.
{: shortdesc}

## Ist IAM für Ihre Instanz aktiviert?
{: #enabled}

Im Laufe der Zeit werden die verwalteten {{site.data.keyword.Db2_on_Cloud_long}}-Datenbankinstanzen in {{site.data.keyword.Bluemix_notm}} für die Verwendung von IAM zur Zugriffssteuerung aktiviert. Führen Sie die folgende Abfrage aus, um zu überprüfen, ob IAM für Ihre Instanz aktiviert ist:

`SELECT CASE WHEN VALUE = 'IBMIAMauth' THEN 1 ELSE 0 END AS IAM_ENABLED FROM SYSIBMADM.DBMCFG WHERE NAME = 'srvcon_gssplugin_list'`

Wenn der zurückgegebene Wert von **IAM_ENABLED** 1 lautet, ist IAM für die Instanz aktiviert.

## Features von IBM Cloud IAM
{: #features}

Die folgenden IAM-Features sind für den verwalteten {{site.data.keyword.Db2_on_Cloud_short}}-Service implementiert, wobei zwei Identitätstypen unterstützt werden:

**IBMid**

Benutzer mit einer IBMid müssen zu jeder Datenbankserviceinstanz vom Datenbankadministrator über die Konsole oder die REST-API hinzugefügt werden, bevor diese Benutzer eine Verbindung zu der betreffenden Datenbankserviceinstanz herstellen können. Wie bei einem Benutzer ohne IBMid muss eine Benutzer-ID für die Datenbankserviceinstanz zu dem Zeitpunkt eingegeben werden, an dem der IBMid-Benutzer hinzugefügt wird. Diese Benutzer-ID muss innerhalb der Datenbankserviceinstanz eindeutig sein. Bei dieser Benutzer-ID handelt es sich auch um die Berechtigungs-ID (AUTH) in der Datenbank. Der Datenbankadministrator kann Berechtigungen auf der Basis der AUTH-ID erteilen und widerrufen

**Service-IDs**

Eine Service-ID identifiziert einen Service oder eine Anwendung in ähnlicher Weise wie eine Benutzer-ID einen Benutzer identifiziert. Die Service-IDs sind IDs, die von Anwendungen für die Authentifizierung bei einem IBM Cloud-Service verwendet werden können. Eine Service-ID stellt eine von der Eigner-IBMid separate Entität dar. Aus diesem Grund können unterschiedliche Autorisierungen und Berechtigungen, die für die Service-ID spezifisch sind, innerhalb der Datenbank erteilt werden. Service-IDs verfügen nicht über Kennwörter. Für jede Service-ID muss ein API-Schlüssel erstellt werden, damit die Service-ID eine Verbindung zur Datenbankserviceinstanz herstellen kann. Weitere Informationen zu Service-IDs finden Sie in [Service-IDs und API-Schlüssel in IBM Cloud IAM - Einführung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/blogs/bluemix/2017/10/introducing-ibm-cloud-iam-service-ids-api-keys/){:new_window}.

## Clientverbindungen und Benutzeranmeldungen
{: #connect_user}

**Voraussetzung**: Db2 Client V11.1 FP3 und höher.

Die folgenden Methoden können für die IAM-Authentifizierung verwendet werden:

**Zugriffstoken**

Die Anwendung kann über die REST-API mithilfe eines API-Schlüssels ein Zugriffstoken direkt beim IAM-Service abrufen. Weitere Informationen finden Sie in [IBM Cloud IAM-Token mithilfe eines API-Schlüssels abrufen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/apikey_iamtoken.html#iamtoken_from_apikey){:new_window}. Das Zugriffstoken verfügt über einen Standardgültigkeitszeitraum von 60 Minuten, bevor es abläuft. Nach dem Ablauf des Tokens lässt der Db2-Server die Herstellung einer Verbindung nicht mehr zu. Nachdem die Verbindung hergestellt ist, wird das Token nicht mehr auf ein Ablaufdatum überprüft. Wie vor der IAM-Integration bleibt die Verbindung bestehen, bis die Anwendung die Verbindung trennt oder die Verbindung aus anderen Gründen beendet wird.

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```

Ein Zugriffstoken identifiziert einen IBMid-Benutzer oder eine Service-ID für die Datenbank. Der Datenbankserver verifiziert die Gültigkeit des Zugriffstokens, bevor er es akzeptiert. Hierbei handelt es sich um die am besten geeignete Methode, wenn die Anwendung Verbindungen zu mehreren Datenbankserviceinstanzen oder zu anderen {{site.data.keyword.Bluemix_notm}}-Serviceinstanzen herstellen muss, da so die für die Validierung des Zugriffstokens erforderliche Kommunikation mit dem IAM-Service auf ein Minimum reduziert wird.

**API-Schlüssel**

Für jeden IBMid-Benutzer bzw. jede Service-ID können mehrere API-Schlüssel erstellt werden. Jeder API-Schlüssel wird normalerweise für eine einzelne Anwendung erstellt. Dies ermöglicht es der Anwendung, eine Verbindung zur Datenbankserviceinstanz herzustellen, vorausgesetzt, die Eigner-IBMid oder Service-ID als Benutzer zur selben Datenbankserviceinstanz hinzugefügt wird. Der API-Schlüssel verfügt in der Datenbank über dieselben Autorisierungen und Berechtigungen wie die Eigner-IBMid oder die Service-ID. Wenn eine Anwendung keine Verbindung mehr mit der Datenbank herstellen können soll, kann der entsprechende API-Schlüssel entfernt werden. Bei dieser Authentifizierungsmethode ist der Änderungsaufwand in der Anwendung geringer als bei der Verwendung eines Zugriffstokens, da keine direkte Interaktion mit dem IAM-Service erforderlich ist. Weitere Informationen zur Erstellung und Verwaltung von API-Schlüsseln finden Sie in [Benutzer-API-Schlüssel verwalten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/docs/iam/userid_keys.html#userapikey){:new_window}.

**IBMid/Kennwort**

Die IBMid und das zugehörige Kennwort können für die Anmeldung bei der Konsole und auch innerhalb der Anwendung in derselben Weise wie eine Benutzer-ID und das zugehörige Kennwort verwendet werden. Eine Ausnahme liegt vor, wenn die IBMid föderiert wird, da eine Umleitung auf die Anmeldeseite Ihrer Organisation nicht möglich ist. Die empfohlene Methode für die Herstellung einer Verbindung zur Datenbankserviceinstanz durch die Anwendung ist jedoch die Verwendung eines Zugriffstokens.

## Unterstützte Schnittstellen
{: #sup-if}

Die folgenden Datenbankclientschnittstellen werden unterstützt:

* [ODBC](#odbc-clpplus)
* [CLP](#odbc-clpplus)
* [CLPPLUS](#odbc-clpplus)
* [JDBC](#jdbc)

### ODBC, CLP und CLPPLUS
{: #odbc-clpplus}

Damit eine ODBC-Anwendung oder ein Befehlszeilenclient (CLP, CLPPLUS) mithilfe der IAM-Authentifizierung eine Verbindung zu einem Db2-Server herstellen kann, muss zuerst ein DSN (Datenquellenname) in einer `db2dsdriver.cfg`-Konfigurationsdatei festgelegt werden. Hierzu den folgenden Befehl ausführen:

`db2cli writecfg add -dsn <dsn_alias> -database <database_name> -host <host_name_or_IP_address> -port 50001 -parameter "Authentication=GSSPLUGIN;SecurityTransportMode=SSL"`

Bei der Konfigurationsdatei `db2dsdriver.cfg` handelt es sich um eine XML-Datei, die sich normalerweise im Verzeichnis `sqllib/cfg` befindet, das eine Liste der DSN-Aliasnamen und der zugehörigen Eigenschaften enthält.

Das folgende Beispiel einer `db2dsdriver.cfg`-Konfigurationsdatei zeigt die Konfigurationen, die für die Herstellung einer Verbindung zu einer Datenbankserviceinstanz verwendet werden. Die Konfigurationsdatei enthält den DSN-Alias, den Datenbanknamen, den Hostnamen (bzw. die IP-Adresse) sowie die Parameterwerte für den Authentifizierungstyp (**Authentication**) und den Sicherheitsübertragungsmodus (**SecurityTransportMode**):

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

* Die ODBC-Verbindungszeichenfolge kann eines der folgenden Elemente enthalten:

    **Zugriffstoken**

    `DSN=<dsn>;ACCESSTOKEN=<access_token>`

    **API-Schlüssel**

    `DSN=<dsn>;APIKEY=<api_key>`

    **IBMid/Kennwort**
    
    `DSN=<dsn>;UID=<ibmid>;PWD=<password>`

    Für ODBC kann **AUTHENTICATION=GSSPLUGIN** entweder in der Konfigurationsdatei `db2dsdriver.cfg` oder in der Verbindungszeichenfolge der Anwendung angegeben werden.

* Die CLP-Anweisung CONNECT kann eines der folgenden Elemente enthalten:

    **Zugriffstoken**

    Stellen Sie eine Verbindung zum Datenbankserver `<database_server_name>` her und übergaben Sie das Zugriffstoken, indem Sie den folgenden Befehl in der Eingabeaufforderung des Befehlszeilenprozessors oder einem Script ausführen:

    `CONNECT TO <database_server_name> ACCESSTOKEN <access_token_string>`

    **API-Schlüssel**

    Stellen Sie eine Verbindung zum Datenbankserver `<database_server_name>` mit einem API-Schlüssel her, indem Sie den folgenden Befehl in der Eingabeaufforderung des Befehlszeilenprozessors oder einem Script ausführen:

    `CONNECT TO <database_server_name> APIKEY <api-key-string>`

    **IBMid/Kennwort**

    Stellen Sie eine Verbindung zum Datenbankserver `<database_server_name>` mit einer IBMid und dem zugehörigen Kennwort her, indem Sie den folgenden Befehl in der Eingabeaufforderung des Befehlszeilenprozessors oder einem Script ausführen:

    `CONNECT TO <database_server_name> USER <IBMid> USING <password>`

    Weitere Details zum Herstellen einer Verbindung zu einem Datenbankserver über den Befehlszeilenprozessor (CLP) finden Sie in [Anweisung CONNECT (Typ 2) ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.sql.ref.doc/doc/r0000908.html){:new_window}. 

* Die CLPPlus-Anweisung CONNECT kann eines der folgenden Elemente enthalten:

    **Zugriffstoken**

    Verbindung zum DSN-Alias herstellen (` @<data_source_name>`) und das Zugriffstoken durch die Ausführung des folgenden Befehls in der CLPPLUS-Eingabeaufforderung oder in einem Script übergeben:

    `connect @<data_source_name> using(accesstoken <access_token_string>)`

    **API-Schlüssel**

    Verbindung zum DSN-Alias herstellen (` @<data_source_name>`) mithilfe eines API-Schlüssels durch die Ausführung des folgenden Befehls in der CLPPLUS-Eingabeaufforderung oder in einem Script:

    `connect @<data_source_name> using(apikey <api-key-string>)`

    **IBMid/Kennwort**

    Verbindung zum DSN-Alias herstellen (` @<data_source_name>`) mithilfe einer IBMid und des zugehörigen Kennworts durch die Ausführung des folgenden Befehls in der CLPPLUS-Eingabeaufforderung oder in einem Script:

    `connect <IBMid>/<password>@<data_source_name>`

    Weitere Einzelheiten zum Herstellen einer Verbindung zu DSN-Aliasnamen mit CLPPLUS finden Sie in [DSN-Aliasnamen in CLPPlus ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.swg.im.dbclient.clpplus.doc/doc/c0057148.html){:new_window}.

### JDBC
{: #jdbc}

JDBC-Treiber des Typs 4 werden für die IAM-Authentifizierung unterstützt.

Die folgenden Beispiele zeigen Verbindungssnippets für die drei Methoden:

**Zugriffstoken**

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

Oder

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:accessToken=<access_token>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**API-Schlüssel**

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

Oder

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:apikey=<api_key>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

**IBMid/Kennwort**

```
DB2SimpleDataSource dataSource;

dataSource.setDriverType( 4 );
dataSource.setDatabaseName( "BLUDB" );
dataSource.setServerName( "<host_name_or_IP_address>" );
dataSource.setPortNumber( 50001 );
dataSource.setSecurityMechanism( com.ibm.db2.jcc.DB2BaseDataSource.PLUGIN_SECURITY );
dataSource.setPluginName( "IBMIAMauth" );
Connection conn = dataSource.getConnection( "<IBMid>", "<password>" );
```

Oder

```
Connection conn = DriverManager.getConnection( "jdbc:db2://<host_name_or_IP_address>:50001/BLUDB:user=<IBMid>;password=<password>;securityMechanism=15;pluginName=IBMIAMauth;sslConnection=true" );
```

## Konsolenbenutzerschnittstelle
{: #console-ux}

Die Anmeldeseite der Servicekonsole bietet die Option für die Anmeldung mit der IBMid und dem zugehörigen Kennwort. Nach dem Klicken auf die Schaltfläche **Anmelden über IBMid** wird der Benutzer zur IAM-Anmeldeseite weitergeleitet, auf der das Kennwort eingegeben wird. Wenn die Authentifizierung abgeschlossen ist, wird der Benutzer zurück an die Konsole weitergeleitet. Bevor eine solche Anmeldung erfolgreich ausgeführt werden kann, muss der Benutzer der IBMid vom Datenbankadministrator über die Konsole oder die REST-API zu jeder Datenbankserviceinstanz hinzugefügt werden. Wie bei einem Benutzer ohne IBMid muss eine Benutzer-ID für die Datenbankserviceinstanz zu dem Zeitpunkt eingegeben werden, an dem der IBMid-Benutzer hinzugefügt wird. Die Benutzer-ID muss innerhalb der Datenbankserviceinstanz eindeutig sein. Bei dieser Benutzer-ID handelt es sich auch um die Berechtigungs-ID (AUTH) in der Datenbank.

## REST-API-Schnittstelle
{: #api}

Die {{site.data.keyword.Db2_on_Cloud_short}}-REST-API wurde erweitert und akzeptiert nun auch ein IAM-Zugriffstoken für die Funktionen, die bisher ein Zugriffstoken akzeptiert haben, das durch einen Datenbankservice generiert wurde.

* Wenn Sie einen neuen IBMid-Benutzer hinzufügen möchten, führen Sie den folgenden Beispiel-API-Aufruf aus:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid>","ibmid":"<userid>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Die Werte von `<userid>` für `"id"` und `"ibmid"` müssen nicht übereinstimmen. Die beiden unterschiedlichen IDs sind in keiner Weise miteinander verknüpft.
  {: note}

* Wenn Sie einen vorhandenen Datenbankbenutzer ohne IBMid (z. B. `abcuser`) migrieren und zu einem IBMid-Benutzer machen möchten, löschen Sie zuerst die Nicht-IBMid-Benutzer-ID, indem Sie den folgenden Beispiel-API-Aufruf ausführen:

  `curl --tlsv1.2 -X DELETE "https://<IPaddress>/dbapi/v3/users/abcuser" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json"`

  Fügen Sie anschließend den Benutzer mit einer IBMid erneut hinzu, die mit der vorherigen Benutzer-ID (`abcuser`) identisch ist, indem Sie den folgenden Beispiel-API-Aufruf ausführen:

  `curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"abcuser","ibmid":"abcuser@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"`

  Da die Benutzer-ID (`abcuser`) für die neue IBMid für diesen Benutzer unverändert bleibt, werden die erteilten Datenbankberechtigungen für den Benutzer nicht geändert. Wenn eine Liste vorhandener Datenbankbenutzer ohne IBMid migriert werden muss, um diese zu IBMid-Benutzern zu machen, müssen Sie die beiden oben beschriebenen API-Aufrufe für jeden Benutzer ausführen.

* Wenn Sie eine große Anzahl neuer IBMid-Benutzer gleichzeitig hinzufügen möchten, erstellen Sie eine Stapeldatei, in der die folgenden Beispiel-API-Aufrufe für die einzelnen Benutzer aufgeführt sind:

  ```
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid1>","ibmid":"<userid1>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  curl --tlsv1.2 "https://<IPaddress>/dbapi/v3/users" -H "Authorization: Bearer <access_token>" -H "accept: application/json" -H "Content-Type: application/json" -d "{"id":"<userid2>","ibmid":"<userid2>@<email_address_domain>","role":"bluadmin","locked":"no","iam":true}"
  .
  .
  .
  ```

Weitere Details zur API des Service finden Sie in [{{site.data.keyword.Db2_on_Cloud_short}}-REST-API ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://ibm.biz/db2oc_api){:new_window}.

## IBMid-Föderierung
{: #fed_ibmid}

Wenn Sie einen eigenen Identitätsprovider wie z. B. LDAP verwenden möchten, müssen Sie zuerst den LDAP-Server mit der IBMid föderieren. Anweisungen zum Föderieren des LDAP-Servers mit der IBMid finden Sie in der Veröffentlichung [IBMid Enterprise Federation Adoption Guide ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.ent.box.com/notes/78040808400?s=nhuzrhlsn0ly338zddomx329tlpmfghc){:new_window}. Nachdem die Föderierung mit der IBMid abgeschlossen ist und die berechtigten Benutzer vom Datenbankadministrator zur Datenbankserviceinstanz hinzugefügt wurden, können sich diese Benutzer mit ihrer Firmenbenutzer-ID und dem zugehörigen Kennwort bei der Konsole anmelden. Alternativ dazu können diese Benutzer ein Zugriffstoken oder einen API-Schlüssel, das bzw. der ihre Benutzer-ID darstellt, verwenden, um über eine der unterstützten Datenbankclientschnittstellen eine Verbindung zur Datenbankserviceinstanz herzustellen.

## Einschränkungen
{: #restrictions}

Hinsichtlich der IAM-Authentifizierung gelten die folgenden Einschränkungen:

* Die IAM-Authentifizierung für einen Db2-Client, der eine Verbindung zu einem Db2-Server herstellt, wird nur über eine SSL-Verbindung unterstützt.
* Die IBMid-Föderierung wird unterstützt, um die Verwendung eines angepassten Benutzerverwaltungsportals oder -servers für die Authentifizierung zu ermöglichen. Diese Unterstützung umfasst keine Föderierung für Gruppen.
* Die IAM-Authentifizierung für die Datenbankföderierung wird nicht unterstützt.
* Die Ausführung von IDA- und UDX-Befehlen (UDX = user-defined extension, benutzerdefinierte Erweiterung) über CLPPlus wird nicht unterstützt.
* JDBC-Treiber des Typs 2 werden nicht unterstützt.




