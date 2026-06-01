---
id: 6a865dea-9fe6-4617-a878-cd86bcf4b86f
title: "Zufallsgraph"
date: 2026-06-01
tags:
  - verteilte_systeme
  - graphentheorie
  - netzwerktopologie
  - peer-to-peer
  - dezentralisierung
  - algorithmen
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Zufallsgraph]]

- **Kernkonzept:** Ein [[Zufallsgraph|Zufallsgraph]] ist ein [[Graph|Graphenmodell]], bei dem [[Kante|Kanten]] zwischen [[Knoten]] mit einer bestimmten Wahrscheinlichkeit existieren. Er modelliert [[Ad-hoc-Netzwerk|Ad-hoc-Netzwerke]] wie unstrukturierte [[Peer-to-Peer-System|Peer-to-Peer-Systeme]], in denen Nachbarbeziehungen zufällig entstehen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Skalierbarkeit]] und [[Robustheit]] in dezentralen [[Netzwerk|Netzwerken]], indem es eine einfache, selbstorganisierende [[Topologie]] ohne zentrale [[Koordination]] ermöglicht. Es erlaubt effiziente [[Suche|Suchalgorithmen]] wie [[Flooding]] oder [[Random Walk]] trotz fehlender Struktur.
- **Abgrenzung & Grenzen:** Zufallsgraphen sind ungeeignet, wenn deterministische [[Zugriffsmuster]] oder garantierte [[Latenz]] erforderlich sind. Alternativen wie [[Strukturierte-P2P-Systeme|strukturierte P2P-Systeme]] (z. B. [[DHT]]) oder [[Super-Peer-Netzwerk|Super-Peer-Architekturen]] bieten hier bessere [[Performanz]], erfordern aber mehr [[Overhead]] für die [[Topologie]]-Pflege.
- **Beispiel / Code:** Modellierung eines unstrukturierten P2P-Netzwerks als Zufallsgraph:
- Jeder [[Knoten]] verwaltet eine Liste von Nachbarn.
- Eine [[Kante]] zwischen zwei Knoten existiert mit Wahrscheinlichkeit p (z. B. p = 0.1).
- Beispiel-Suche via Flooding:
  ```
  function floodSearch(node, query, ttl):
      if ttl <= 0 or query in node.seen:
          return
      node.seen.add(query)
      if node.hasData(query):
          return node.data
      for neighbor in node.neighbors:
          floodSearch(neighbor, query, ttl - 1)
  ```
