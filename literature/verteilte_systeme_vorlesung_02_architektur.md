---
id: "a1b2c3d4-e5f6-4789-b012-3456789abcde"
title: "Vorlesung: Architekturen verteilter Systeme"
date: 2023-10-15
tags:
  - verteilte_systeme
  - vorlesung
  - lektürenotiz
  - literature
source: "subjects/distributed_systems/video/02-Architektur.mp4"
---

# Vorlesung: Architekturen verteilter Systeme

- **Quelle:** `subjects/distributed_systems/video/02-Architektur.mp4`
- **Fach:** Distributed Systems

---

## 🏗️ Einführung in Architekturen verteilter Systeme

*Timestamp im Video:* `00:00:00 - 00:05:00`

**Zusammenfassung des Dozenten:**
- Architekturen dienen der Problemlösung unter Berücksichtigung spezifischer Anforderungen und Einschränkungen wie Zeit und finanzielle Mittel.
- Architekturstile beeinflussen maßgeblich die Gestaltung eines Systems durch Prinzipien, die den Architekturplan prägen.
- Verteilte Systeme bestehen aus Hardware- und Softwareanteilen, die auf autonomen Recheneinheiten laufen.
- Unterscheidung zwischen logischer Struktur der Software (Software-Architektur) und der Verteilung auf Hardware (System-Architektur bzw. Deployment).
- Architekturstile in der Software-Architektur umfassen Komponenten, Konnektoren, Daten und Konfigurationen.

**Referenzierte Zettel:**
- [[Software-Architektur]]
- [[System-Architektur]]
- [[Architekturstil]]

---

## 🧱 Software-Architekturen und Architekturstile

*Timestamp im Video:* `00:05:01 - 00:23:50`

**Zusammenfassung des Dozenten:**
- Geschichtete Architekturen bestehen aus Schichten, die durch Request-Reply-Down-Calls verbunden sind. Strikte Schichtung erlaubt nur Kommunikation mit der direkt darunterliegenden Schicht.
- Objektbasierte Architekturen nutzen Objekte mit gekapseltem Zustand und definierten Schnittstellen, was die Verteilung im System verbirgt.
- Serviceorientierte Architekturen (SOA) basieren auf der Komposition von Diensten, die über operationale Schnittstellen angeboten werden.
- Ressourcenbasierte Architekturen (REST) nutzen einheitliche Schnittstellen für alle Ressourcen, was Robustheit und Skalierbarkeit fördert.
- REST-Architekturen verwenden HTTP-Operationen (GET, POST, PUT, DELETE) für den Zugriff auf Ressourcen und sind zustandslos.

**Referenzierte Zettel:**
- [[Geschichtete Architektur]]
- [[Objektbasierte Architektur]]
- [[Serviceorientierte Architektur (SOA)]]
- [[REST-Architektur]]
- [[HTTP-Methoden]]

---

## 🔄 Koordination und Kommunikation in verteilten Systemen

*Timestamp im Video:* `00:23:51 - 00:51:43`

**Zusammenfassung des Dozenten:**
- Komponenten in verteilten Systemen müssen sich gegenseitig finden (referenzielle Kopplung) und zeitlich abstimmen (temporale Kopplung).
- Direkte Verbindungen erfordern sowohl referenzielle als auch temporale Kopplung.
- Vermittler wie Mailboxen oder Nachrichtenwarteschlangen ermöglichen zeitliche Entkopplung.
- Publish-Subscribe-Systeme ermöglichen referenzielle Entkopplung durch Themen (Topics) und Ereignis-Busse.
- Geteilte Datenräume (z.B. Linda-Tupelräume) bieten maximale Entkopplung durch persistente Speicherung von Nachrichten.

**Referenzierte Zettel:**
- [[Referenzielle Kopplung]]
- [[Temporale Kopplung]]
- [[Publish-Subscribe-System]]
- [[Linda-Tupelraum]]
- [[Middleware]]

---

## 🧩 Middleware und Architekturmuster

*Timestamp im Video:* `00:51:44 - 01:01:28`

**Zusammenfassung des Dozenten:**
- Middleware dient als Basis zur Vereinfachung der Realisierung verteilter Systeme und bietet Lösungen für typische Problemstellungen.
- Adapter und Wrapper werden genutzt, um inkompatible Schnittstellen zu verbinden und Transparenz herzustellen.
- Broker reduzieren die Anzahl benötigter Adapter durch zentrale Vermittlung zwischen Komponenten.
- Interceptor-Muster ermöglichen die flexible Erweiterung von Middleware-Funktionen durch das Einfügen optionaler Zusatzfunktionen.
- Interceptor können z.B. für Replikation oder Verschlüsselung genutzt werden, ohne die Grundfunktionalität der Middleware zu ändern.

**Referenzierte Zettel:**
- [[Middleware]]
- [[Adapter und Wrapper]]
- [[Broker-Architektur]]
- [[Interceptor-Muster]]

---

## 🖥️ Systemarchitekturen: Zentralisierte und dezentralisierte Modelle

*Timestamp im Video:* `01:01:29 - 01:20:56`

**Zusammenfassung des Dozenten:**
- Systemarchitekturen beschreiben die Verteilung von Softwarekomponenten auf Recheneinheiten.
- Zentralisierte Architekturen (Client-Server-Modell) bestehen aus wenigen Servern und vielen Clients, die über Request-Reply kommunizieren.
- Zweischichtige (Two-Tier) und dreischichtige (Three-Tier) Architekturen verteilen logische Schichten auf unterschiedliche Rechnerknoten.
- Thin Clients und Fat Clients repräsentieren die Extreme der Verteilung von Benutzerschnittstelle und Anwendungslogik.
- Peer-to-Peer-Systeme (P2P) sind dezentralisiert, wobei alle Knoten gleichberechtigt sind und Ressourcen gemeinsam nutzen.

**Referenzierte Zettel:**
- [[Client-Server-Modell]]
- [[Two-Tier-Architektur]]
- [[Three-Tier-Architektur]]
- [[Thin Client]]
- [[Fat Client]]
- [[Peer-to-Peer (P2P)]]

---

## 🌐 Strukturierte und unstrukturierte Peer-to-Peer-Systeme

*Timestamp im Video:* `01:20:57 - 01:35:17`

**Zusammenfassung des Dozenten:**
- Strukturierte P2P-Systeme nutzen deterministische Overlay-Netzwerke (z.B. Ring, Hypercube) für effiziente Suche nach Ressourcen.
- Distributed Hash Tables (DHT) ermöglichen die Zuordnung von Daten zu Knoten über semantikfreie Schlüssel.
- Chord ist ein Beispiel für ein strukturiertes P2P-System mit Ringtopologie und logarithmischer Suchkomplexität.
- Unstrukturierte P2P-Systeme nutzen zufällige Overlay-Netzwerke und Suchstrategien wie Flooding oder Random Walk.
- Super-Peers kombinieren zentrale und dezentrale Ansätze, indem sie spezielle Aufgaben wie Indexierung übernehmen.

**Referenzierte Zettel:**
- [[Strukturierte P2P-Systeme]]
- [[Distributed Hash Table (DHT)]]
- [[Chord-Algorithmus]]
- [[Unstrukturierte P2P-Systeme]]
- [[Super-Peer]]

---

## 🌍 Kombinierte Architekturen: Edge Server und kollaborative Systeme

*Timestamp im Video:* `01:35:18 - 01:41:35`

**Zusammenfassung des Dozenten:**
- Edge-Server-Architekturen platzieren Server am Rand des Internets, um Latenzen für Endanwender zu reduzieren.
- Content Delivery Networks (CDNs) nutzen Edge-Server, um Medieninhalte nah an den Nutzern bereitzustellen.
- Fog Computing erweitert Cloud-Dienste durch virtualisierte Ressourcen am Netzwerkrand für zeitkritische Anwendungen.
- Kollaborative Systeme (z.B. BitTorrent) motivieren Endknoten zur aktiven Teilnahme durch Anreizmechanismen.
- BitTorrent nutzt Tracker zur Koordination und verteilt Dateien in Segmenten, die unter den Teilnehmern ausgetauscht werden.

**Referenzierte Zettel:**
- [[Edge-Server-Architektur]]
- [[Content Delivery Network (CDN)]]
- [[Fog Computing]]
- [[Kollaborative verteilte Systeme]]
- [[BitTorrent]]