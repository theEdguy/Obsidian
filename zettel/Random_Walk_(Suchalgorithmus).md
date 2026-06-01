---
id: 18669477-1ab9-43d4-a2da-cd0da2f86cb0
title: "Random Walk (Suchalgorithmus)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - suchalgorithmus
  - peer-to-peer
  - dezentralisierung
  - netzwerk
  - unstrukturierte_systeme
  - zufallsgraph
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Random Walk (Suchalgorithmus)]]

- **Kernkonzept:** Ein [[Suchalgorithmus|Suchalgorithmus]] in [[unstrukturiertes_Peer-to-Peer-System|unstrukturierten Peer-to-Peer-Systemen]], bei dem eine [[Anfrage]] von Knoten zu Knoten zufällig weitergeleitet wird, bis das gesuchte [[Datenelement]] gefunden oder ein Abbruchkriterium erreicht ist.
- **Nutzen & Zweck:** Reduziert den [[Nachrichtenaufwand]] im Vergleich zu [[Flooding]] und vermeidet die [[Netzwerküberlastung]], indem es die [[Anfrage]] nicht an alle [[Nachbarn]] verbreitet, sondern nur an einen zufällig ausgewählten. Besonders nützlich in [[dezentralisierten_Systemen|dezentralisierten Systemen]] mit dynamischer Topologie.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn eine garantierte [[Erfolgsrate]] oder geringe [[Latenz]] erforderlich ist, da die Suche länger dauern kann als bei [[Flooding]] oder [[strukturierten_Peer-to-Peer-Systemen|strukturierten Ansätzen]]. Im Vergleich zu [[Super-Peer-Netzwerken]] fehlt die Möglichkeit, [[Indexierung|indizierte Suchanfragen]] effizient zu nutzen. Bei sehr großen [[Netzwerken]] kann die [[Sucheffizienz]] stark sinken.
- **Beispiel / Code:** Pseudocode für einen einfachen Random-Walk-Algorithmus:

function randomWalk(startNode, query, ttl):
    currentNode = startNode
    hops = 0
    while hops < ttl:
        if currentNode.hasData(query):
            return currentNode
        neighbors = currentNode.getNeighbors()
        currentNode = random.choice(neighbors)
        hops += 1
    return None  // Anfrage erfolglos
