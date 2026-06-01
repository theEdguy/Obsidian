---
id: df7dfc84-4ec5-49ec-be0b-0610ee7aec92
title: "Flooding (Suchalgorithmus)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - suchalgorithmus
  - peer-to-peer
  - netzwerk
  - dezentralisierung
  - verteilte-systeme
  - unstrukturiert
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Flooding (Suchalgorithmus)]]

- **Kernkonzept:** Flooding ist ein [[Suchalgorithmus|Suchalgorithmus]] in [[unstrukturiert|unstrukturierten]] [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], bei dem ein [[Knoten]] eine [[Anfrage]] an alle seine [[Nachbarn]] weiterleitet, die diese rekursiv wiederholen, bis die gesuchte [[Ressource]] gefunden oder ein Abbruchkriterium erreicht ist.
- **Nutzen & Zweck:** Flooding löst das Problem der [[Ressourcenlokalisierung]] in dezentralen Netzwerken ohne zentrale [[Indexierung]], indem es eine einfache, aber robuste [[Breitensuche]] durchführt. Es eignet sich besonders für kleine bis mittelgroße Netzwerke, in denen keine [[Struktur]] vorgegeben ist.
- **Abgrenzung & Grenzen:** Flooding sollte nicht in großen Netzwerken eingesetzt werden, da es zu hohem [[Netzwerkverkehr]] und [[Skalierbarkeitsproblemen]] führt. Alternativen wie [[Random Walk]] oder [[Super-Peer-Netzwerke]] sind effizienter, wenn die [[Latenz]] oder der [[Datenverkehr]] kritisch sind. Zudem ist Flooding ungeeignet für [[strukturierte Peer-to-Peer-Systeme]], die gezielte [[Routing-Algorithmen]] nutzen.
- **Beispiel / Code:** ```python
# Pseudocode für Flooding in einem P2P-Knoten
def handle_query(query, ttl, visited_nodes):
    if query in local_resources:
        return "Ressource gefunden"
    if ttl <= 0 or node_id in visited_nodes:
        return "Abbruch"
    visited_nodes.add(node_id)
    for neighbor in neighbors:
        neighbor.handle_query(query, ttl - 1, visited_nodes.copy())
```
*Erläuterung*: Der [[Knoten]] prüft lokal nach der [[Ressource]] und leitet die [[Anfrage]] bei Misserfolg an alle [[Nachbarn]] weiter, bis die [[Time-To-Live (TTL)]] erschöpft ist oder die [[Ressource]] gefunden wird.
