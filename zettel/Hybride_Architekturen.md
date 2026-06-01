---
id: 71cc38f9-c28d-4dd7-8e99-4840ef759d40
title: "Hybride Architekturen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - hybrid
  - skalierbarkeit
  - peer-to-peer
  - content_delivery
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Hybride Architekturen]]

- **Kernkonzept:** Hybride Architekturen kombinieren Elemente [[dezentralisiertes_System|dezentralisierter]] und [[zentralisiertes_System|zentralisierter]] [[Architektur|Architekturen]], um die Vorteile beider Ansätze zu nutzen, z. B. durch [[Super-Peer|Super-Peers]] oder [[Edge-Server|Edge-Server]].
- **Nutzen & Zweck:** Sie lösen das Problem der Skalierbarkeit und Effizienz in [[verteilte_Systeme|verteilten Systemen]], indem sie [[Koordination|koordinierte]] Strukturen (z. B. [[Tracker|Tracker]] in BitTorrent) mit [[dezentrale_Organisation|dezentraler Organisation]] verbinden, um [[Performanz|Performanz]] und [[Ausfallsicherheit|Ausfallsicherheit]] zu verbessern.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn vollständige [[Dezentralisierung|Dezentralisierung]] (z. B. für [[Zensurresistenz|Zensurresistenz]]) oder strikte [[Symmetrie|Symmetrie]] (wie in reinen [[Peer-to-Peer-Systeme|Peer-to-Peer-Systemen]]) erforderlich ist. Unterscheidet sich von rein [[unstrukturierte_P2P-Systeme|unstrukturierten P2P-Systemen]] durch hierarchische oder teilzentralisierte [[Kontrollmechanismen|Kontrollmechanismen]].
- **Beispiel / Code:** BitTorrent nutzt eine hybride Architektur:
1. **Zentraler Tracker**: Koordiniert initiale [[Peer|Peers]]-Suche (zentralisiert).
2. **Schwarm-Prinzip**: [[Daten|Daten]] werden direkt zwischen [[Peer|Peers]] getauscht (dezentral).

Beispiel-Torrent-Datei (vereinfacht):
```
{
  "announce": "http://tracker.example.com/announce",
  "info": {
    "name": "Beispieldatei.iso",
    "piece length": 262144,
    "pieces": "<Hashes>",
    "length": 104857600
  }
}
```
