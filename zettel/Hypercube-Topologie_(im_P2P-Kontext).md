---
id: 1aaaef95-389f-46ec-b1cd-6de34308b27d
title: "Hypercube-Topologie (im P2P-Kontext)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - p2p
  - netzwerk_topologie
  - dht
  - routing
  - skalierbarkeit
  - dezentralisierung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Hypercube-Topologie (im P2P-Kontext)]]

- **Kernkonzept:** Die Hypercube-Topologie ist eine [[strukturierte_Peer-to-Peer-Systeme|strukturierte_P2P-Topologie]], bei der [[Knoten|Knoten]] in einem [[n-dimensionalen_Würfel|n-dimensionalen Hyperwürfel]] organisiert sind, um effizientes [[Routing]] und [[Nachschlagen]] von [[Daten|Daten]] zu ermöglichen.
- **Nutzen & Zweck:** Sie löst das Problem der skalierbaren und deterministischen [[Datenverteilung]] in [[dezentralisierte_Systeme|dezentralisierten Systemen]], indem sie eine logische Struktur bietet, die [[Schlüssel-Wert-Paare]] mit minimalem Aufwand (O(log n) Hops) auffindbar macht. Besonders nützlich für [[verteilte_Hash-Tabellen]] (DHTs) in [[P2P-Netzwerke|P2P-Netzwerken]].
- **Abgrenzung & Grenzen:** Nicht geeignet für hochdynamische Netzwerke mit häufigen [[Knotenausfällen]], da die starre Topologie aufwändige Rekonfiguration erfordert. Unterscheidet sich von [[unstrukturierte_Peer-to-Peer-Systeme|unstrukturierten P2P-Systemen]] (z. B. Gnutella) durch deterministisches Routing, von [[Ring-Topologien]] (z. B. Chord) durch höhere Konnektivität und kürzere Pfadlängen. Weniger flexibel als [[Overlay-Netzwerke]] mit adaptiven Routing-Algorithmen.
- **Beispiel / Code:** Ein 3-dimensionaler Hypercube (8 Knoten) mit binären Bezeichnern (000 bis 111):
- Jeder Knoten ist mit 3 Nachbarn verbunden (z. B. 000 mit 001, 010, 100).
- Nachschlagen eines Schlüssels *k* (z. B. 101):
  1. Starte bei Knoten 000.
  2. Routing erfolgt durch schrittweises Korrigieren der Bits (z. B. 000 → 100 → 101).
  3. Zielknoten 101 speichert das (Schlüssel, Wert)-Paar.

Pseudocode für Routing:
```
def route(key, current_node):
    if current_node.id == key:
        return current_node
    # Finde das nächste Bit, das sich unterscheidet
    for i in range(len(key)):
        if current_node.id[i] != key[i]:
            next_node = flip_bit(current_node.id, i)
            return route(key, next_node)
```
