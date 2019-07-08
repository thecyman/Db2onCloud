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

# Konnektivitätsoptionen
{: #connect_options}

{{site.data.keyword.Db2_on_Cloud_long}} bietet abhängig von den Anforderungen Ihrer Anwendungsverbindung mehrere sichere Konnektivitätsoptionen.  
{: shortdesc}

## Verbindung zu einem öffentlichen Endpunkt herstellen (Standardoption)
{: #pub_endpt}

Wie bei jedem öffentlichen Cloud-Service können Sie Ihre Anwendung über einen öffentlichen Hostnamen verbinden, der dann angegeben wird, wenn Ihr Service bereitgestellt wird. Der Zugriff auf Ihre Daten wird durch strikte Authentifizierung, umfangreiche Db2-Berechtigungsoptionen und Zugriffssteuerung, Verschlüsselung für die Datenübertragung und für ruhende Daten sowie durch Verfahren zur Sicherheit und Konformität von IBM für Entwicklung und Betrieb geschützt. Optionales IP-Whitelisting wird angeboten. Erstellen Sie einen IBM Supportfall, wenn Sie IP-Whitelisting aktivieren möchten.

### Verbindung zu einem öffentlichen Endpunkt herstellen:
{: #pub_endpt_steps}

Der einfachste Weg, um eine Verbindung zu Ihren Daten herzustellen, besteht darin, den Namen des öffentlichen Hosts zu verwenden, der in Ihrem Begrüßungsschreiben angegeben wurde. Sie können Ihren Hostnamen und die Berechtigungsnachweise auch auf die folgende Weise erhalten:

1. Melden Sie sich bei {{site.data.keyword.Db2_on_Cloud_short}} an und klicken Sie auf Ihre Serviceinstanz.
2. Klicken Sie auf **Serviceberechtigungsnachweise**.
3. Klicken Sie auf **Neuer Berechtigungsnachweis** und anschließend auf **Hinzufügen**.
4. Nachdem die Berechtigungsnachweise erstellt wurden, klicken Sie unter der Spalte `Aktionen` auf **Berechtigungsnachweise anzeigen**.
5. Notieren Sie in dem folgenden JSON-Dokumentbeispiel den Inhalt der Felder für Hostname, Kennwort und Benutzername. Sie verwenden diese drei Komponenten bei der Herstellung der Verbindung zum öffentlichen Endpunkt:

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

   ![Öffentlicher Netzzugriff auf {{site.data.keyword.cloud_notm}}](images/public_connection.png "Grafische Ansicht einer Benutzer-zu-Cloud-Verbindung")

## Verbindung zu einem privaten Endpunkt herstellen: IBM Cloud-Serviceendpunkt
{: #priv_endpt}

Wenn Sie in Ihrem {{site.data.keyword.cloud_notm}}-Konto eine Anwendung bereitgestellt haben und diese mit Ihrer Datenbank verbinden möchten, ohne dass der Datenverkehr über öffentliche Netze fließt, können Sie die Option **{{site.data.keyword.cloud_notm}}-Serviceendpunkt** beim Bestellen Ihrer Datenbank verwenden. Wenn der Service bereitgestellt wird, wird Ihnen ein privater Hostname angegeben, zu dem Sie nur innerhalb Ihres {{site.data.keyword.cloud_notm}}-Kontos eine Verbindung herstellen können.  

Weitere Informationen zur Option des {{site.data.keyword.cloud_notm}}-Serviceendpunkts finden Sie in [Serviceendpunkt: Produktinformationen](/docs/services/service-endpoint?topic=service-endpoint-about#about).


### Verbindung zu einem privaten Endpunkt mit IBM Cloud-Serviceendpunkt herstellen
{: #priv_endpt_steps}

Die Kommunikation mit privaten Netzen und Endpunkten erfolgt über den {{site.data.keyword.cloud_notm}}-Serviceendpunktservice. Der Serviceendpunktservice erleichtert eine schnelle und sichere Weiterleitung des Datenverkehrs im Netz zwischen unterschiedlichen {{site.data.keyword.cloud_notm}}-Services und Ihrer Datenbank über das private Netzbackplane von {{site.data.keyword.cloud_notm}}. Diese Weiterleitung im Netz gewährleistet, dass Ihre Daten niemals in das öffentliche Internet gelangen. 

Voraussetzung für den Einstieg in die Nutzung des Serviceendpunkts ist, dass Ihr {{site.data.keyword.cloud_notm}}-Konto für VRF (Virtual Routing and Forwarding) aktiviert ist. Informationen dazu, wie Sie Ihr Konto aktivieren können, finden Sie in [Ihr Konto mit IBM Cloud CLI für Serviceendpunkt aktivieren](/docs/services/service-endpoint?topic=service-endpoint-getting-started#cs_cli_install_steps).

Nachdem Ihr Konto für VRF aktiviert wurde und der Serviceendpunkt aktiviert ist, befolgen Sie die Anweisungen in Ihrem Begrüßungsschreiben.

Jetzt ist es an der Zeit, Ihre {{site.data.keyword.Db2_on_Cloud_short}}-Instanz ausgehend von Ihrem {{site.data.keyword.cloud_notm}}-Konto mithilfe der privaten Netzadresse zu verbinden, die in Ihrem Begrüßungsschreiben angegeben ist.

## Verbindung zu einem privaten Endpunkt herstellen: VPN (Virtual Private Network)
{: #vpn}

Wenn Sie eine Anwendung in einem privaten Netz bereitgestellt haben, dass sich außerhalb von {{site.data.keyword.cloud_notm}} befindet und keinen Zugang zum öffentlichen Internet hat, müssen Sie es über ein virtuelles privates Netz (VPN) mit Ihrer Datenbank verbinden. Sie können die Anforderung dann stellen, wenn Sie den Service bestellen oder indem Sie einen IBM Supportfall öffnen. Netzentwickler von IBM unterstützen Ihre Netzentwickler beim Einrichten eines VPN-Tunnels zwischen Ihrem privaten Netz und {{site.data.keyword.cloud_notm}}.

### Verbindung zu einem privaten Endpunkt mit einem VPN herstellen
{: #priv_endpt_vpn_steps}

Um eine VPN-Verbindung zu Ihren Clouddaten hinter einem öffentlichen Endpunkt herzustellen, [erstellen Sie einen {{site.data.keyword.cloud_notm}}-Supportfall](https://cloud.ibm.com/unifiedsupport/cases/add){:external}, der folgende Details enthält:

* **Art des Supports**: Technisch 
* **Kategorie**: Datenbanken 
* **Angebot**: Wählen Sie Ihre {{site.data.keyword.Db2_on_Cloud_short}}-Instanz aus. 
* **Betreff**: VPN-Verbindungsanforderung 
* **Beschreibung**: Geben Sie die folgenden erforderlichen Informationen an.
  * **Kundenseitige VPN Peer-Adresse** (Ihr VPN-Endpunkt): `<IP Address>`
  * **Kundenseitige Verschlüsselungsdomäne** (geben Sie genau an, was erforderlich ist – 10.0.0.0/8 kann nicht bearbeitet werden, das die Adressierung 10 auch innerhalb von {{site.data.keyword.cloud_notm}} für Back-End-Services verwendet wird): `<Domain>`
  * **Kundenseitige VPN-Hardware & Version**: `<Hardware and Version number>`
  * **Kundenseitiger VPN-Kontakt** (Ansprechpartner mit Name und E-Mail-Adresse): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Optional** (Nur ändern, wenn die folgenden Standardwerte nicht geeignet sind):

  *IKE/ISAKMP-Parameter (Phase I)*

  * **Verschlüsselungsverfahren**: IKEv1
  * **IKE-Verschlüsselung / Verschlüsselungsalgorithmus**: AES-256
  * **Authentifizierungsalgorithmus**: SHA1
  * **DH-Gruppe**: Gruppe 5
  * **Security Association-Lebensdauer (Sekunden)**: 1d (86400 Sekunden)

  *IPSEC-Parameter (Phase II)*

  * **IPsec-Verschlüsselung / Verschlüsselungsalgorithmus**: AES-256
  * **Authentifizierungsalgorithmus**: SHA1
  * **DH-Gruppe** (bei Verwendung von PF-Secrecy): Gruppe 5
  * **Security Association-Lebensdauer (Sekunden)**: 3600 Sekunden

Nach dem Eingang Ihrer Anforderung werden {{site.data.keyword.cloud_notm}}-Techniker die entsprechenden Firewall-Ports öffnen und die angegebene IP-Adresse in die Whitelist aufnehmen. Die Kommunikation und Auflösung der Anforderung erfolgt über ein {{site.data.keyword.cloud_notm}}-Supportfallticket.

![Öffentlicher Netzzugriff auf {{site.data.keyword.cloud_notm}} über VPN](images/public_connection_vpn.png "Grafische Ansicht einer Benutzer-zu-Cloud-Verbindung")
