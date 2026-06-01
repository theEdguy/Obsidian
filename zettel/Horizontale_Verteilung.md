---
id: 0e7be84c-7693-4097-b8d2-ac6601c21e68
title: "Horizontale Verteilung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - skalierbarkeit
  - datenpartitionierung
  - peer-to-peer
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Horizontale Verteilung]]

- **Kernkonzept:** Bei der horizontalen Verteilung wird ein [[Client]] oder [[Server]] physisch in logisch äquivalente [[Teil|Teile]] zerlegt, die jeweils mit einer eigenen [[Partition]] des vollständigen [[Datensatz|Datensatzes]] arbeiten. Dies ermöglicht eine parallele Verarbeitung und Skalierung.
- **Nutzen & Zweck:** Das Konzept löst das Problem der [[Skalierbarkeit]] und [[Lastverteilung]] in verteilten Systemen. Es ermöglicht, große [[Datensatz|Datensätze]] oder [[Anfrage|Anfragen]] effizient zu verarbeiten, indem die [[Arbeitslast]] auf mehrere [[Knoten]] verteilt wird.
- **Abgrenzung & Grenzen:** Horizontale Verteilung ist nicht geeignet, wenn die [[Daten]] stark voneinander abhängig sind oder eine zentrale [[Koordination]] erfordern. Im Gegensatz zur [[vertikalen Verteilung]] (Schichtung) wird hier keine funktionale Trennung vorgenommen, sondern eine Aufteilung der [[Daten]] oder [[Anfrage|Anfragen]]. Bei kleinen Systemen kann der [[Overhead]] der Verteilung den Nutzen überwiegen.
- **Beispiel / Code:** Ein Beispiel ist ein verteiltes [[Datenbank|Datenbanksystem]], bei dem die Tabellen horizontal partitioniert werden. Jeder [[Server]] verwaltet einen Teil der Daten:

Server 1: Benutzer mit IDs 1-1000
Server 2: Benutzer mit IDs 1001-2000
Server 3: Benutzer mit IDs 2001-3000

Anfragen werden an den jeweiligen Server weitergeleitet, der die passende [[Partition]] verwaltet.
