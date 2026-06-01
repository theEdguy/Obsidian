---
id: 208570ee-5ad6-4f54-8bd5-4bb2f9566bde
title: "Flooding-basiertes Multicasting"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - verteilte-systeme
  - multicast
  - flooding
  - kommunikation
  - algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Flooding-basiertes Multicasting]]

- **Kernkonzept:** Flooding-basiertes Multicasting ist ein Verfahren zur Verbreitung von [[Nachricht|Nachrichten]] in einem [[Netzwerk]], bei dem jeder [[Knoten]] eine empfangene Nachricht an alle seine [[Nachbar|Nachbarn]] weiterleitet, außer an den Absender und nur, wenn die Nachricht noch nicht bekannt ist.
- **Nutzen & Zweck:** Es löst das Problem der effizienten und robusten Verbreitung von [[Information|Informationen]] in unstrukturierten oder dynamischen [[Netzwerk|Netzwerken]], ohne zentrale Steuerung oder komplexe [[Routing-Tabelle|Routing-Tabellen]]. Besonders nützlich in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]] oder bei hoher [[Knoten|Knoten]]-Dynamik.
- **Abgrenzung & Grenzen:** Nicht geeignet für große [[Netzwerk|Netzwerke]] mit vielen [[Knoten|Knoten]], da es zu hoher [[Netzlast]] und [[Redundanz]] führt. Im Vergleich zu [[baum-basiertem Multicasting]] oder [[gossip-basierten Protokollen]] ist es weniger skalierbar. Alternativen wie [[Application-Level Multicasting (ALM)]] oder [[Message-Queuing-Systeme]] bieten bessere Kontrolle über [[Nachrichtenfluss|Nachrichtenflüsse]] und [[Ressourcenauslastung]].
- **Beispiel / Code:** Pseudocode für Flooding-basiertes Multicasting:

function onReceive(message, sender):
    if not seen(message):
        markAsSeen(message)
        for neighbor in neighbors:
            if neighbor != sender:
                send(message, neighbor)

// Initialer Aufruf:
send(message, allNeighbors)
