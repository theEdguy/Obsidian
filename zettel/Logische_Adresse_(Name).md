---
id: 140aa636-34e8-4fa2-9f3a-a4d7cb6c7d2e
title: "Logische Adresse (Name)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte_kommunikation
  - message_queuing
  - namensauflösung
  - middleware
  - routing
  - abstraktion
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Logische Adresse (Name)]]

- **Kernkonzept:** Eine logische Adresse (auch [[Name|Namen]]) dient in [[verteilte Systeme|verteilten Systemen]] als abstrakte Referenz auf eine [[Queue|Warteschlange]] oder einen [[Queue Manager|Queue-Manager]], unabhängig von dessen physischer Netzwerkadresse. Sie ermöglicht die Entkopplung von [[Sender|Sendern]] und [[Empfänger|Empfängern]] durch indirekte Adressierung.
- **Nutzen & Zweck:** Logische [[Adresse|Adressen]] lösen das Problem der direkten Abhängigkeit von physischen Netzwerkadressen in [[Message-Queuing-Systeme|Message-Queuing-Systemen]]. Sie ermöglichen flexible [[Routing|Routen]], dynamische Umkonfigurationen und vereinfachen die [[Administration]] durch zentrale [[Namensauflösung]] in [[Datenbank|Datenbanken]] mit Kontaktadressen.
- **Abgrenzung & Grenzen:** Logische [[Adresse|Adressen]] sind ungeeignet für Systeme mit strikten Echtzeitanforderungen oder direkter [[Punkt-zu-Punkt-Kommunikation]], da die zusätzliche [[Namensauflösung]] Latenz verursacht. Alternativen wie direkte IP-Adressierung oder [[MPI]]-basierte Kommunikation bieten hier geringere [[Overhead|Overheads]]. Zudem erfordern sie eine zentrale [[Infrastruktur]] (z. B. [[Queue Manager]]), was in dezentralen [[Peer-to-Peer-Systeme|Peer-to-Peer-Systemen]] problematisch sein kann.
- **Beispiel / Code:** In IBM MQ wird eine logische Adresse wie `LA1` in einer Alias-Tabelle auf eine lokale Queue `QMA` abgebildet. Der Queue Manager löst diese Adresse über eine Routing-Tabelle auf, um Nachrichten an die physische Queue `SQ1` eines entfernten Queue Managers `QMB` zu senden:

```
Alias Tabelle:
LA1 → QMA

Routing Tabelle (QMA):
QMA → SQ1 (lokal)
QMB → SQ1 (remote)
```
Die Nachricht wird dann über einen [[Channel]] an `QMB` weitergeleitet, ohne dass der Sender die physische Adresse von `QMB` kennen muss.
