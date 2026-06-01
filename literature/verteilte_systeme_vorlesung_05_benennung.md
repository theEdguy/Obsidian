---
id: "a1b2c3d4-e5f6-4789-8a0b-123456789012"
title: "Vorlesung: Benennung in verteilten Systemen"
date: 2023-10-15
tags:
  - verteilte_systeme
  - vorlesung
  - lektürenotiz
  - literature
source: "subjects/distributed_systems/video/05-Benennung.mp4"
---

# Vorlesung: Benennung in verteilten Systemen

- **Quelle:** `subjects/distributed_systems/video/05-Benennung.mp4`
- **Fach:** Distributed Systems

---

## 🔖 Einführung in die Benennung

*Timestamp im Video:* `00:00:13 - 00:05:14`

- **Zweck der Benennung:**
  - Vergabe von Namen für Einheiten in verteilten Systemen (z.B. Prozesse, Hosts, Ressourcen, Kommunikationskanäle).
  - Namen ermöglichen den Zugriff und die Referenzierung dieser Einheiten.
- **Arten von Namen:**
  - **Menschfreundliche Namen:** Leicht merkbar, z.B. DNS-Namen.
  - **Technische Namen/Adressen:** Effizient für Systemzugriffe, z.B. IP-Adressen.
- **Namensauflösung:**
  - Prozess der Umwandlung von benutzerfreundlichen Namen in technische Adressen.
  - Erfordert ein Namenssystem, das die systematische Beziehung zwischen Namen und Adressen verwaltet.
- **Ortsabhängigkeit von Namen:**
  - Ortsabhängige Namen (Adressen) können sich ändern, z.B. bei Mobilität von Prozessen oder Hosts.
  - Ortsunabhängige Namen (z.B. Identifier) bleiben konstant und verweisen dauerhaft auf dieselbe Einheit.
- **Beispiel aus der Praxis:**
  - Vergleich mit Telefonnummern: Eine Person behält ihren Namen, aber die Telefonnummer (Adresse) kann sich ändern.

**Referenzierte Zettel:**
- [[Namensauflösung]]
- [[Verteilungstransparenz]]
- [[Adressierung in Netzwerken]]

---

## 🏷️ Grundbegriffe und Arten von Namen

*Timestamp im Video:* `00:05:14 - 00:20:59`

- **Entitäten und Zugriffspunkte:**
  - Entitäten in verteilten Systemen (z.B. Hosts, Prozesse, Dateien) benötigen Zugriffspunkte, die durch Adressen benannt werden.
  - Adressen sind Namen von Zugriffspunkten und ermöglichen den Zugriff auf die Entität.
- **Identifier (Bezeichner):**
  - Eindeutige, ortsunabhängige Namen zur Identifikation von Entitäten.
  - Eigenschaften: Ein Identifier verweist auf genau eine Entität, jede Entität hat genau einen Identifier, und Identifier sollten nicht wiederverwendet werden.
- **Reine Namen vs. Hierarchische Namen:**
  - **Reine Namen:** Zeichenketten ohne inhärente Bedeutung, z.B. numerische Prozess-IDs.
  - **Hierarchische Namen:** Strukturierte Namen mit semantischer Bedeutung, z.B. DNS-Namen wie `www.example.com`.
- **Mobilität von Entitäten:**
  - Heimatstandort (Home Agent) ermöglicht die Weiterleitung von Anfragen an temporäre Adressen mobiler Entitäten.
  - Beispiel: Mobile IP in IPv6 nutzt Heimatstandorte zur Verwaltung mobiler Hosts.
- **Probleme mit Mobilität:**
  - Dauerhafte Heimatadressen können ineffizient werden, wenn sich der Standort einer Entität permanent ändert.
  - Lösung: Nutzung von DNS-Namen zur Auflösung der Heimatadresse.

**Referenzierte Zettel:**
- [[Identifier in verteilten Systemen]]
- [[DNS (Domain Name System)]]
- [[Mobile IP]]
- [[Heimatstandort (Home Agent)]]

---

## 🔄 Namensauflösung für lineare Namen

*Timestamp im Video:* `00:21:00 - 00:44:49`

- **Broadcasting als einfacher Mechanismus:**
  - Anfragen werden an alle Knoten im Netzwerk gesendet, um den Standort einer Entität zu ermitteln.
  - Problem: Skaliert schlecht in großen Netzwerken und verursacht hohe Last.
  - Beispiel: ARP (Address Resolution Protocol) im lokalen Netzwerk.
- **Verteilte Hashtabellen (DHTs):**
  - Strukturierte Peer-to-Peer-Netzwerke (z.B. Chord) nutzen verteilte Hashtabellen zur effizienten Namensauflösung.
  - Knoten sind in einem Ring angeordnet, und die Namensauflösung erfolgt durch Routing im Ring.
  - Finger-Tabellen ermöglichen effizientes Routing in logarithmischer Zeit.
- **Hierarchische Ansätze (HLS):**
  - Namensraum wird in verschachtelte Domänen unterteilt, die jeweils einen Verzeichnisknoten besitzen.
  - Namensauflösung beginnt an einem Blattknoten und arbeitet sich nach oben, bis die Entität gefunden wird.
  - Änderungen im Namensraum werden ebenfalls hierarchisch propagiert.
- **Beispiel: Chord-Ring:**
  - Jeder Knoten kennt seinen Nachfolger und zusätzliche Knoten in exponentiell wachsenden Abständen (Finger-Tabelle).
  - Namensauflösung erfolgt durch schrittweises Weiterleiten der Anfrage im Ring.

**Referenzierte Zettel:**
- [[Broadcasting in Netzwerken]]
- [[Verteilte Hashtabellen (DHT)]]
- [[Chord-Protokoll]]
- [[Hierarchische Namensauflösung]]

---

## 🌳 Hierarchische Benennung und Namenssysteme

*Timestamp im Video:* `00:45:00 - 01:10:17`

- **Strukturierte Namen:**
  - Hierarchische Namen bestehen aus einer Folge von Segmenten, z.B. `home/steffen/mailbox`.
  - Benennungsgraphen repräsentieren die Struktur des Namensraums (gerichteter, beschrifteter Graph).
- **Namensauflösung in hierarchischen Systemen:**
  - Auflösung beginnt an einem Startknoten (z.B. Wurzel) und folgt den Kanten des Graphen.
  - Beispiel: Dateisysteme oder DNS nutzen hierarchische Namensauflösung.
- **Alias-Namen:**
  - **Hardlinks:** Mehrere Pfade verweisen auf denselben Knoten im Benennungsgraphen.
  - **Softlinks/Symbolische Links:** Verweisen auf einen anderen Namen, der erneut aufgelöst werden muss.
- **Implementierung von Namensräumen:**
  - Kleine Namensräume können durch eine zentrale Datenbank verwaltet werden.
  - Große, verteilte Namensräume erfordern eine Verteilung auf mehrere Nameserver.
  - Drei Ebenen der Implementierung:
    - **Globale Schicht:** Wurzel und Top-Level-Domains (z.B. `.com`, `.de`).
    - **Administrative Schicht:** Organisationseinheiten (z.B. `uni-karlsruhe.de`).
    - **Management-Schicht:** Konkrete Einheiten (z.B. Hosts, Dateien).

**Referenzierte Zettel:**
- [[Hierarchische Namenssysteme]]
- [[DNS (Domain Name System)]]
- [[Alias-Namen (Hardlinks und Softlinks)]]
- [[Verzeichnisdienste]]

---

## 🌐 DNS: Ein Beispiel für hierarchische Benennung

*Timestamp im Video:* `01:24:55 - 01:31:20`

- **Struktur des DNS:**
  - Baumstruktur mit Wurzelknoten, Top-Level-Domains (TLDs), Domänen und Hosts.
  - Beispiel: `ev-lk301.hs-karlsruhe.de` besteht aus mehreren Segmenten, die durch Punkte getrennt sind.
- **Zonen und Nameserver:**
  - Jede Zone (z.B. `hs-karlsruhe.de`) wird von einem oder mehreren Nameservern verwaltet.
  - Nameserver speichern Resource Records (z.B. A-Records für IP-Adressen, MX-Records für Mailserver).
- **Namensauflösung im DNS:**
  - **Iterative Auflösung:** Client fragt nacheinander verschiedene Nameserver an.
  - **Rekursive Auflösung:** Nameserver leiten Anfragen weiter und sammeln die Ergebnisse.
  - Caching von Ergebnissen reduziert die Last auf Nameserver und verbessert die Performance.
- **Skalierbarkeit und Performance:**
  - Globale Nameserver (z.B. Root-Server) nutzen Replikation und Caching für hohe Verfügbarkeit.
  - Administrative und Management-Schichten nutzen weniger Replikation, aber schnellere Antwortzeiten.

**Referenzierte Zettel:**
- [[DNS-Architektur]]
- [[Resource Records in DNS]]
- [[Iterative vs. rekursive Namensauflösung]]
- [[Caching in verteilten Systemen]]

---

## 📂 Attributbasierte Benennung und Verzeichnisdienste

*Timestamp im Video:* `01:31:20 - 01:41:16`

- **Attributbasierte Suche:**
  - Ermöglicht die Suche nach Entitäten anhand ihrer Attribute (z.B. "alle Mailserver der Informatik-Fakultät").
  - Problem: Aufwendige Suche, da alle Entitäten überprüft werden müssen.
- **LDAP (Lightweight Directory Access Protocol):**
  - Verzeichnisdienst, der hierarchische Benennung mit attributbasierter Suche kombiniert.
  - Verzeichniseinträge bestehen aus Attribut-Wert-Paaren und sind eindeutig benannt.
  - Beispiel: Ein Eintrag für `cn=mailserver, ou=cs, o=vu, c=nl` enthält Attribute wie IP-Adressen und Hostnamen.
- **Operationen in LDAP:**
  - **Read:** Liest die Attribute eines Verzeichniseintrags.
  - **List:** Listet alle untergeordneten Einträge eines Verzeichnisknotens auf.
  - **Search:** Sucht nach Einträgen, die bestimmte Attribute erfüllen.
- **Effizienz durch Hierarchie:**
  - Die hierarchische Struktur reduziert den Suchraum und beschleunigt die Suche.
  - Indexierungsserver können die Suche weiter optimieren.

**Referenzierte Zettel:**
- [[Attributbasierte Benennung]]
- [[LDAP (Lightweight Directory Access Protocol)]]
- [[Verzeichnisdienste]]
- [[Indexierung in verteilten Systemen]]