---
id: "f8a5d3b7-2c1e-4d6f-8e9a-1b2c3d4e5f6a"
title: "Vorlesung: Kommunikation in Verteilten Systemen"
date: "2023-11-15"
tags:
  - verteilte_systeme
  - vorlesung
  - lektürenotiz
  - literature
source: "subjects/distributed_systems/video/04-Kommunikation.mp4"
---

# Vorlesung: Kommunikation in Verteilten Systemen

- **Quelle:** `subjects/distributed_systems/video/04-Kommunikation.mp4`
- **Fach:** Verteilte Systeme

---

## 🌐 Einführung in die Kommunikation in Verteilten Systemen

*Timestamp im Video:* `00:00:13 - 00:08:53`

**Zusammenfassung des Dozenten:**
- Verteilte Systeme bestehen aus Prozessen, die auf verschiedenen Recheneinheiten ablaufen und durch Nachrichtenaustausch interagieren.
- Kommunikation erfolgt über Netzwerkmechanismen, da kein gemeinsamer Speicher existiert.
- Das OSI-Referenzmodell (Open Systems Interconnection) strukturiert die Kommunikation in sieben Schichten, wobei jede Schicht spezifische Protokolle und Dienste definiert.
  - Die unteren Schichten (1-4) umfassen physikalische Übertragung, Sicherung, Vermittlung und Transport.
  - Die oberen Schichten (5-7) beinhalten Sitzungsmanagement, Datenrepräsentation und anwendungsspezifische Protokolle.
- Das OSI-Modell dient als theoretische Grundlage, während in der Praxis häufig der TCP/IP-Protokollstapel genutzt wird.
- Nachteile des OSI-Modells: Fehlende Zugriffstransparenz, unnötige Funktionalitäten (z. B. Sitzungs- und Darstellungsschicht) und Beschränkung auf einfache binäre Nachrichten.

**Referenzierte Zettel:**
- [[OSI-Referenzmodell]]
- [[TCP/IP-Protokollstapel]]
- [[Verteilungstransparenz]]
- [[Prozesskommunikation]]

---

## 📡 Grundlagen der Datenkommunikation und Schichtenmodelle

*Timestamp im Video:* `00:08:54 - 00:20:20`

**Zusammenfassung des Dozenten:**
- Die **Bitübertragungsschicht** (Physical Layer) realisiert die physikalische Übertragung von Bits über Medien wie Strom oder Funk.
  - Definiert Hardware-Formate, Steckerbelegungen und Signalinterpretation.
- Die **Sicherungsschicht** (Data Link Layer) erkennt und korrigiert Übertragungsfehler durch Prüfsummen und Flusskontrolle.
  - Verwendet Frames zur Strukturierung der Datenübertragung.
- Die **Vermittlungsschicht** (Network Layer) übernimmt das Routing in komplexen Netzwerken und die Adressierung von Knoten.
  - Bekanntestes Protokoll: IP (Internet Protocol).
- Die **Transportschicht** (Transport Layer) bietet anwendungsorientierte Dienste zur Nachrichtenübertragung.
  - Wichtige Protokolle: TCP (verbindungsorientiert) und UDP (verbindungslos).
  - TCP garantiert zuverlässige, geordnete Datenübertragung, während UDP schneller, aber unzuverlässig ist.
- Middleware-Mechanismen wie Remote Procedure Calls (RPC) oder Message-Oriented Middleware (MOM) erweitern die Funktionalität der Transportschicht.

**Referenzierte Zettel:**
- [[Bitübertragungsschicht]]
- [[Sicherungsschicht]]
- [[Vermittlungsschicht]]
- [[Transportschicht]]
- [[TCP vs. UDP]]
- [[Middleware]]

---

## 🔄 Kommunikationsmiddleware: Persistenz und Synchronität

*Timestamp im Video:* `00:20:21 - 00:30:51`

**Zusammenfassung des Dozenten:**
- Kommunikationsmiddleware bietet höhere Abstraktionsebenen als reine Netzwerkprotokolle.
- **Persistente Kommunikation** speichert Nachrichten zwischen, sodass Sender und Empfänger nicht gleichzeitig aktiv sein müssen (z. B. E-Mail-Systeme).
- **Transiente Kommunikation** verwirft Nachrichten, wenn der Empfänger nicht erreichbar ist (z. B. TCP/IP).
- **Synchrone Kommunikation** blockiert den Sender bis zur Antwort des Empfängers (z. B. RPC).
- **Asynchrone Kommunikation** ermöglicht dem Sender die Fortsetzung der Ausführung nach dem Absenden der Nachricht (z. B. Message Queues).
- Typische Kombinationen:
  - Client-Server-Systeme: Transient und synchron.
  - Message-Oriented Middleware: Persistent und asynchron.

**Referenzierte Zettel:**
- [[Persistente Kommunikation]]
- [[Transiente Kommunikation]]
- [[Synchrone Kommunikation]]
- [[Asynchrone Kommunikation]]
- [[Client-Server-Modell]]
- [[Message-Oriented Middleware]]

---

## 🖥️ Remote Procedure Calls (RPC)

*Timestamp im Video:* `00:30:52 - 00:57:42`

**Zusammenfassung des Dozenten:**
- RPC ermöglicht den Aufruf von Prozeduren auf entfernten Rechnern, als wären sie lokal.
- **Stubs** (Client- und Server-Stub) übersetzen lokale Aufrufe in Netzwerknachrichten und umgekehrt.
  - **Marshalling** kodiert Parameter in ein übertragbares Format.
  - **Unmarshalling** dekodiert empfangene Nachrichten in lokale Datenstrukturen.
- Parameterübergabe erfolgt immer nach dem **Call-by-Value**-Prinzip, da entfernte Referenzen nicht sinnvoll sind.
- Varianten von RPC:
  - **1-Way-RPC**: Keine Antwort erwartet, sofortige Fortsetzung des Clients.
  - **Verzögerter synchroner RPC**: Client erhält Bestätigung des Serverstarts und wartet auf Callback mit dem Ergebnis.
- Beispiel: **DCE-RPC** (Distributed Computing Environment) verwendet eine Interface Definition Language (IDL) zur Spezifikation von Prozedurschnittstellen.
  - UUIDs (Universal Unique Identifiers) identifizieren Schnittstellen eindeutig.
  - QManager und Verzeichnisdienste unterstützen das Binden von Clients und Servern.

**Referenzierte Zettel:**
- [[Remote Procedure Call (RPC)]]
- [[Marshalling und Unmarshalling]]
- [[Call-by-Value vs. Call-by-Reference]]
- [[DCE-RPC]]
- [[UUID]]

---

## 📦 Message-Oriented Middleware (MOM) und Message Queues

*Timestamp im Video:* `00:57:43 - 01:42:06`

**Zusammenfassung des Dozenten:**
- MOM realisiert persistente, asynchrone Kommunikation über Warteschlangen (Message Queues).
- Nachrichten werden in Warteschlangen eingestellt und vom Empfänger abgeholt, sobald dieser verfügbar ist.
- **Operationen**:
  - `Put`: Nachricht in eine Warteschlange einstellen.
  - `Get`: Blockierendes Abholen einer Nachricht.
  - `Poll`: Nicht-blockierendes Abfragen einer Nachricht.
  - `Notify`: Registrierung eines Callbacks für neue Nachrichten.
- **Message Broker** vermitteln zwischen inkompatiblen Protokollen oder Nachrichtenformaten.
  - Unterstützen Themen-basiertes Routing (Publish/Subscribe) und inhaltliche Analyse von Nachrichten.
- Beispiel: **IBM MQ** (ehemals WebSphere MQ) verwendet QManager zur Verwaltung von Warteschlangen und Kanälen (Channels) zur Nachrichtenübertragung.
  - Routing-Tabellen und Alias-Tabellen ermöglichen flexible Adressierung.
  - Nachrichten können bis zu 100 MB groß sein und werden über Overlay-Netzwerke von QManagern verteilt.

**Referenzierte Zettel:**
- [[Message-Oriented Middleware (MOM)]]
- [[Message Queue]]
- [[Message Broker]]
- [[Publish-Subscribe-Modell]]
- [[IBM MQ]]

---

## 🌍 Multicast-Kommunikation

*Timestamp im Video:* `01:42:07 - 02:02:00`

**Zusammenfassung des Dozenten:**
- **Multicast** bezeichnet die Übertragung einer Nachricht von einem Sender an mehrere Empfänger.
- In lokalen Netzwerken ist Multicast effizient durch Broadcast-Mechanismen realisierbar.
- In Weitverkehrsnetzen (z. B. Internet) erfordert Multicast die Definition von Routen oder Overlay-Netzwerken.
- **Overlay-Netzwerke** auf Anwendungsebene ermöglichen Multicast durch:
  - **Baumstrukturen**: Effiziente Verteilung mit minimalem Nachrichtenaufwand.
  - **Mesh-Netzwerke**: Robustere Verteilung durch redundante Verbindungen.
- Beispiel: **Chord** (strukturiertes P2P-Netzwerk) kann zur Konstruktion von Multicast-Bäumen genutzt werden.
  - Knoten treten einer Multicast-Gruppe bei, indem sie den zuständigen Knoten (Successor) im Chord-Ring finden.
- Metriken zur Bewertung von Overlay-Netzwerken:
  - **Link-Stress**: Anzahl der Durchläufe einer physikalischen Verbindung.
  - **Stretch**: Verhältnis des Kommunikationsaufwands im Overlay zum optimalen Weg.

**Referenzierte Zettel:**
- [[Multicast]]
- [[Overlay-Netzwerk]]
- [[Baumstruktur vs. Mesh-Netzwerk]]
- [[Chord]]
- [[Link-Stress und Stretch]]

---

## 🦠 Epidemische Protokolle und Datenverbreitung

*Timestamp im Video:* `02:02:01 - 02:37:54`

**Zusammenfassung des Dozenten:**
- **Epidemische Protokolle** verbreiten Daten in verteilten Systemen nach dem Vorbild der Ausbreitung von Krankheiten.
- Anwendungsfall: Verteilte Datenbanken, bei denen Änderungen an allen Knoten repliziert werden müssen.
- Zwei Hauptmodelle:
  - **Anti-Entropy**: Knoten tauschen in regelmäßigen Abständen Aktualisierungen mit zufälligen Partnern aus.
    - Varianten: Push, Pull, Push-Pull.
    - Push-Pull ist am effizientesten und skaliert gut (log(N) Runden für vollständige Verbreitung).
  - **Gossiping**: Knoten verbreiten neue Informationen an zufällige Nachbarn, bis die Verbreitung mit einer Wahrscheinlichkeit P_stop abbricht.
    - Effizient, aber nicht alle Knoten erhalten garantiert die Information.
- **Löschen von Daten** erfordert spezielle Mechanismen wie **Totenscheine**, um das Löschen als Aktualisierung zu repräsentieren.
  - Totenscheine müssen ausreichend lange im System verbleiben, um vollständige Verbreitung zu garantieren.

**Referenzierte Zettel:**
- [[Epidemische Protokolle]]
- [[Anti-Entropy-Modell]]
- [[Gossiping]]
- [[Totenschein (Tombstone)]]