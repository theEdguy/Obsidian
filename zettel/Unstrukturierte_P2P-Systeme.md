---
id: edc41440-00f6-4eae-b6ad-1f4659373d09
title: "Unstrukturierte P2P-Systeme"
date: 2026-06-01
tags:
  - verteilte_systeme
  - peer-to-peer
  - verteilte-systeme
  - netzwerk-topologie
  - dezentralisierung
  - suche-algorithmen
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Unstrukturierte P2P-Systeme]]

- **Kernkonzept:** Unstrukturierte [[Peer-to-Peer-System|Peer-to-Peer-Systeme]] organisieren [[Knoten|Knoten]] in einem zufälligen [[Overlay-Netzwerk|Overlay-Netzwerk]], bei dem jeder [[Knoten]] eine Ad-hoc-Liste von [[Nachbarn]] verwaltet, ohne feste Topologie oder zentrale Steuerung.
- **Nutzen & Zweck:** Sie ermöglichen dezentrale [[Suche|Suchvorgänge]] und [[Ressourcen|Ressourcenteilung]] in verteilten Systemen, ohne Abhängigkeit von zentralen [[Servern]] oder [[Indizes]]. Besonders nützlich für dynamische Netzwerke mit häufigen [[Knoten|Knotenänderungen]], da sie keine aufwendige Strukturpflege erfordern.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendungen]], die garantierte [[Suche|Suchergebnisse]] oder effiziente Skalierbarkeit erfordern. Im Vergleich zu [[strukturierten P2P-Systemen]] (z. B. [[DHTs]]) oder [[Super-Peer-Netzwerken]] sind sie weniger performant bei großen [[Datenmengen]] oder präzisen [[Anfragen]]. Flooding-basierte [[Suche|Suchstrategien]] erzeugen hohe Netzlast.
- **Beispiel / Code:** Flooding-basierte Suche in Pseudocode:

function search(node, query, ttl):
    if ttl <= 0 or query in node.seen_queries:
        return
    node.seen_queries.add(query)
    if node.has_resource(query):
        return node.address
    for neighbor in node.neighbors:
        result = search(neighbor, query, ttl - 1)
        if result:
            return result
    return None
