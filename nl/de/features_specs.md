---

copyright:
  years: 2014, 2019
lastupdated: "2019-06-12"

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

# Features & und Spezifikationen
{: #fs}

{{site.data.keyword.Db2_on_Cloud_long}}-Features und -Spezifikationen sind zur besseren Übersichtlichkeit im Folgenden zusammengefasst.
{: shortdesc}


| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Db2 AESE | J | Db2 v11.1.3.3 |
| Leseoperation in der Bereitschaftsdatenbank | J | Nur ausgelagerter DR-Knoten |
| Automatische rollierende Aktualisierungen | J | Bei HA-Plänen |
| Optionen für den Standort des Rechenzentrums | J | [Standorte](https://ibm.biz/db2oncloud-locations){:external}. Siehe auch: Bereitstellungs- & Skalierungsdauer. |
| BLU (speicherintern) | J | Standardwert ist 'Zeile', `CREATE TABLE..AS COL` für BLU angeben |
| Activity Tracker | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Rootzugriff verfügbar | N | Db2 Hosted verwenden, falls Rootzugriff erforderlich ist |
{: class="simple-tab-table"}
{: caption="Tabelle 1. Allgemein" caption-side="top"}
{: #simpletabtable1}
{: tab-title="General"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| DR (ausgelagert) | J | - |
| Hochverfügbarkeit (2 Knoten in 1 Zone) | J | SLA: 99,99 % Verfügbarkeitszeit |
| Unterschiedliche Zonen im selben Rechenzentrum | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | **Hinweis**: HADR an einem anderen Standort wird unterstützt. |
| Change Data Capture (CDC) | J | - |
| Lokal als HADR verwenden | N | CDC verwenden. Weitere Informationen finden Sie in [Wie können Daten von Db2 in Db2 on Cloud migriert oder synchronisiert werden?](https://developer.ibm.com/answers/questions/426111/how-can-i-migrate-from-db2-to-db2-on-cloud/){:external}. |
| Autonome Funktionsübernahme - HA | J | - |
| Autonome Funktionsübernahme - DR (ausgelagert) | N | Schaltfläche oder API verwenden |
| IP-Wechsel bei Funktionsübernahme | J | Nur lokale HA; keine ausgelagerte HADR |
| RPO: Hohe Verfügbarkeit | 0 s | HA ist synchron |
| RTO: Hohe Verfügbarkeit | Normalerweise 0 - 10 min | Mit Wiederholungscode, stellt sich als Verzögerung bei Db2 ACR dar |
| RPO: HADR auf einem ausgelagerten Knoten | Normalerweise < 15 s | Ausgelagerte DR ist asynchron |
| RTO: HADR auf einem ausgelagerten Knoten | < 3 min | Initiierung mit Konsolenschaltfläche oder API erforderlich |
{: class="simple-tab-table"}
{: caption="Tabelle 2. Hochverfügbarkeit & Replikation" caption-side="top"}
{: #simpletabtable2}
{: tab-title="High availability & replication"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Max. RAM und Cores | 1 TB RAM, 48 Cores | Für Precise Performance XL-Plan gültig. |
| Max. Speicher | 11 TB | Für Precise Performance XL-Plan gültig. Plattenspeicher für Daten und Protokolle. |
| Flex: Basisplan | 4 GB RAM, 1 Core, 2 GB Plattenspeicher | - |
| Flex: Max. RAM und Cores | 128 GB RAM, 32 Cores | Höhere Spezifikationen erforderlich? Precise Performance-Plan verwenden oder IBM Support kontaktieren. |
| Flex: Max. Speicher | 4 TB | Plattenspeicher für Daten und Protokolle. Höhere Spezifikationen erforderlich? Precise Performance-Plan verwenden oder IBM Support kontaktieren. |
{: class="simple-tab-table"}
{: caption="Tabelle 3. Systemkonfigurationen" caption-side="top"}
{: #simpletabtable3}
{: tab-title="System configurations"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Hochverfügbarkeitspläne | 99,99 % | - |
| Einzelserverpläne | 99,5 % | - |
| Ausgelagerter DR-Knoten | 99,5 % | Zusätzlich lokale HA erforderlich, um 99,99 % zu erreichen |
| Wartungsrichtlinie | J | [Details lesen](https://developer.ibm.com/answers/questions/439146/where-can-i-find-detail-about-maintenance-and-noti.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabelle 4. Wartungsrichtlinien & SLAs" caption-side="top"}
{: #simpletabtable4}
{: tab-title="Maintenance policies & SLAs"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| HIPAA-Ready | J | Alle kostenpflichtigen Pläne einschließlich Flex. Muss den HIPAA-Modus von IBM Support anfordern. |
| HITRUST  | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | Db2 Hosted kann zum gegenwärtigen Zeitpunkt für HITRUST verwendet werden. |
| International Organization for Standardization (ISO)  | J | ISO 27001, 27002, 27017 und 27018 |
| Service Organization Controls (SOC) | J | SOC 2 Typ 2 |
| DSGVO | J | - |
| EU Cloud | J | Region Frankfurt verwenden. Unterstützung wird physisch in der EU bereitgestellt. |
| Umfassende Compliance-Liste | J | [Einhaltung von Sicherheitsvorgaben](https://www.ibm.com/support/knowledgecenter/en/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/compliances.html){:external} |
{: class="simple-tab-table"}
{: caption="Tabelle 5. Einhaltung von Sicherheitsvorgaben" caption-side="top"}
{: #simpletabtable5}
{: tab-title="Security compliances"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Tägliche Sicherungen | J | 14 Tage mit täglichen Sicherungen |
| Zeitpunktgesteuerte Recovery (Self-Service) | Verfügbar ab 15. Nov. 2018 | [Zeitpunktgesteuerte Wiederherstellung](/docs/services/Db2onCloud?topic=Db2onCloud-bnr#point-in-time) |
| Ausgelagerte Sicherungen | Auf Anfrage | Ab 01. Dez. 2018 standardmäßig ausgelagert.  |
| Sicherung bis zu 10 Jahre aufbewahren | Auf Anfrage | Ab 01. Dez. 2018. Support-Ticket erforderlich. |
| Alte Daten ohne Wiederherstellung abfragen | J | Einrichten von [Time Travel Query](https://developer.ibm.com/answers/questions/426878/how-do-i-use-time-travel-query-in-db2-or-db2-on-cl.html){:external} erforderlich. |
{: class="simple-tab-table"}
{: caption="Tabelle 6. Sicherung & Wiederherstellung" caption-side="top"}
{: #simpletabtable6}
{: tab-title="Backup & restore"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Single-Tenant-VM | J | Alle kostenpflichtigen Pläne, einschließlich Flex, beziehen sich auf Single-Tenant-VMs oder Bare-Metal-Systeme. |
| ICIAE | J | Bei IBM Support anfordern. Wenn ICIAE für eine vorhandene Serviceumgebung angefordert wird, müssen die Daten von IBM Support in Ihre ICIAE-Umgebung migriert werden. |
| VPN | J | Bei IBM Support anfordern. |
| Verschlüsselung auf Platte | J | -  |
| SSL/TLS-Verbindungen | J | -  |
| IP-Whitelisting | Einige | Auf Db2-Benutzerebene verfügbar. Für die Netzebene ICIAE o. ä. in Betracht ziehen.  |
| Key Protect (BYOK) | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| MIS/vernetzter Service | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - |
| Grenzwert für maximale Anzahl gleichzeitiger Verbindungen: **Kostenfreier Plan** | J | Maximal 5 Verbindungen  |
| Grenzwert für maximale Anzahl gleichzeitiger Verbindungen: **Kostenpflichtige Pläne** | N | Unbegrenzte Anzahl von Verbindungen  |
{: class="simple-tab-table"}
{: caption="Tabelle 7. Netzbetrieb, Sicherheit & VMs" caption-side="top"}
{: #simpletabtable7}
{: tab-title="Networking, security, & VMs"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| BYOL-Rabatte | J | [Ankündigung](https://ibm.biz/db2oncloud-byol){:external} |
| In IBM Cloud verfügbar | J | Sowohl Abonnement als auch nutzungsabhängig |
| Mit Bestellung eines Softwareangebots verfügbar | J | Alle Pläne einschließlich Flex. [Bestandteile & Details](https://ibm.biz/db2oncloud-parts-public){:external}|
| In Hybrid Data Management Platform (HDMP) verfügbar | J | Nur Flex-Plan. [Details zu HDMP](https://www.ibm.com/ca-en/marketplace/hybrid-data-management-platform){:external}|
| Tägliche Abrechnung | J | Die Abrechnung für Flex-Pläne basiert auf dem Spitzenwert der täglichen Nutzung. Beispiel: Bei einem Scale-up von 2 auf 8 Cores für eine Stunde eines Tages werden nur für diesen Tag 8 Cores in Rechnung gestellt, 2 Cores für alle anderen Tage des Monats. |
| Stündliche Abrechnung | [In Roadmap](https://ibm.biz/db2oncloud-roadmap){:external} | - | 
| Hauptsächliche Preismetrik | Monatlich | Preise werden auf monatlicher Basis angegeben (Beispiel: $ 189 USD pro Monat). Ein anteilmäßiger monatlicher Preis basiert für einen aktivierten Service auf der Anzahl der Tage pro Monat, in denen der Service beendet wurde. [Beispiele](/docs/services/Db2onCloud?topic=Db2onCloud-plans_pricing#examples) |
{: class="simple-tab-table"}
{: caption="Tabelle 8. Preisstruktur & Kauf" caption-side="top"}
{: #simpletabtable8}
{: tab-title="Pricing & purchasing"}
{: tab-group="fs"}

| Feature | Unterstützt? | Kommentare |
|---------|------------|----------|
| Dallas | **Bereitstellung**: < 5 Minuten. **Skalierung**: < 45 Minuten. | Nur Flex-Plan, abhängig vom Bestand |
| USA (Süden) (sonstige) | **Bereitstellung**: 1 Tag. **Skalierung**: 8 Stunden. | Geringere Dauer an bestimmten Standorten. |
| Frankfurt & London | **Bereitstellung**: < 5 Minuten. **Skalierung**: 2 Stunden. | Nur Flex-Plan, abhängig vom Bestand |
| EU (sonstige) | **Bereitstellung**: 3 - 5 Tage. **Skalierung**: 1 - 2 Tage. | Geringere Dauer an bestimmten Standorten. |
| Sydney | **Bereitstellung**: < 1 Stunde. **Skalierung**: 2 Stunden. | Nur Flex-Plan, abhängig vom Bestand |
| Asien-Pazifik (sonstige) | **Bereitstellung**: 3 - 5 Tage. **Skalierung**: 3 - 5 Tage. | Geringere Dauer an bestimmten Standorten. Geringere Volumen führen in der Region Asien-Pazifik zu langsamerer Bereitstellungszeit. |
{: class="simple-tab-table"}
{: caption="Tabelle 9. Bereitstellungs- & Skalierungsdauer" caption-side="top"}
{: #simpletabtable9}
{: tab-title="Deployment & scaling durations"}
{: tab-group="fs"}

