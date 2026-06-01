---
id: 36851281-6ecf-4774-8660-da4fb15c5629
title: "Successor (im Chord-Ring)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - peer-to-peer
  - chord
  - dht
  - routing
  - hashing
  - netzwerk-topologie
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Successor (im Chord-Ring)]]

- **Kernkonzept:** Der [[Successor|Successor]] im [[Chord-Ring]] ist der [[Knoten]], der im [[Ring]]-basierten [[Overlay-Netzwerk]] den kleinsten [[Bezeichner]] besitzt, der größer oder gleich einem gegebenen [[Schlüssel]] ist. Er ist verantwortlich für die Speicherung der [[Datenelemente]] mit diesem [[Schlüssel]].
- **Nutzen & Zweck:** Der [[Successor]] löst das Problem der effizienten [[Datenverteilung]] und [[Suche]] in [[dezentralisierten Systemen|dezentralisierten Systemen]]. Er ermöglicht es, [[Datenelemente]] in einem [[verteilten Hash-Tabelle|verteilten Hash-Tabellen]]-System (DHT) wie [[Chord]] schnell zu lokalisieren und zu speichern, ohne zentrale [[Koordination]].
- **Abgrenzung & Grenzen:** Der [[Successor]]-Ansatz ist nicht geeignet für [[Systeme]], die keine [[Ring]]-Topologie nutzen oder keine [[Hash-Funktion|Hash-Funktionen]] zur [[Schlüssel]]-Generierung einsetzen. Im Vergleich zu unstrukturierten [[Peer-to-Peer-Systemen|Peer-to-Peer-Systemen]] erfordert [[Chord]] eine präzise [[Knoten]]-Organisation und [[Routing]]-Tabellen, was bei hoher [[Knoten]]-Fluktuation zu erhöhtem [[Overhead]] führen kann.
- **Beispiel / Code:** Im [[Chord-Ring]] mit [[Knoten]]-Bezeichnern von 0 bis 2^m-1:
- Ein [[Datenelement]] mit [[Schlüssel]] 5 wird im [[Successor]]-Knoten mit dem kleinsten [[Bezeichner]] ≥ 5 gespeichert.
- Beispiel: Bei [[Knoten]] mit den [[Bezeichnern]] 1, 3, 6, 9 ist der [[Successor]] von [[Schlüssel]] 5 der [[Knoten]] mit [[Bezeichner]] 6.
- Ein [[Lookup]]-Algorithmus nutzt [[Finger-Tabellen]], um den [[Successor]] effizient zu finden, z. B. lookup(3)@9 → 28 → 1 → 4.
