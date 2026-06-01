---
id: b26b2917-c17e-455d-8005-daf88069f26c
title: "Alias Tabelle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte_kommunikation
  - message_queuing
  - routing
  - ibm_mq
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Alias Tabelle]]

- **Kernkonzept:** Eine [[Alias Tabelle|Alias-Tabelle]] ist eine Datenstruktur in [[Message-Queuing System|Message-Queuing-Systemen]], die logische [[Queue|Queues]]-Namen auf lokale oder entfernte [[Queue|Queues]] abbildet, um [[Routing|das Routing]] von Nachrichten zu vereinfachen.
- **Nutzen & Zweck:** Sie löst das [[Problem]] der manuellen [[Adressierung]] in verteilten [[System|Systemen]], indem sie eine Abstraktionsschicht für [[Nachrichten]]-Ziele bereitstellt. Dadurch müssen [[Anwendung|Anwendungen]] keine physischen [[Queue|Queues]]-Standorte kennen und können flexibel auf Änderungen in der [[Infrastruktur]] reagieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Systeme]], die dynamisches [[Routing]] erfordern, da [[Alias Tabellen|Alias-Tabellen]] statisch konfiguriert werden. Alternativen wie [[Message Broker]] oder [[Publish-Subscribe]]-Mechanismen bieten mehr Flexibilität, sind aber komplexer. In [[MPI]]-basierten [[System|Systemen]] (transiente Kommunikation) sind [[Alias Tabellen|Alias-Tabellen]] irrelevant, da dort direkte [[Prozess]]-Adressierung genutzt wird.
- **Beispiel / Code:** Beispiel aus IBM MQ:

Alias Tabelle:
LA1 → QMA
LA2 → QMC

Routing Tabelle (QMA):
QMA → SQ1
QMC → SQ2

Eine Nachricht an LA1 wird von QMA in die lokale Queue SQ1 oder an QMC (für SQ2) weitergeleitet, abhängig von der Routing-Konfiguration.
