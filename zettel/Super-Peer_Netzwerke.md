---
id: 09fc3128-b9c8-47b2-8037-281c96b4d73c
title: "Super-Peer Netzwerke"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - peer-to-peer
  - hierarchie
  - skalierbarkeit
  - koordination
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Super-Peer Netzwerke]]

- **Kernkonzept:** Super-Peer Netzwerke sind [[hierarchisch|hierarchische]] [[Peer-to-Peer System|Peer-to-Peer-Systeme]], die [[symmetrisch|symmetrische]] [[Struktur|Strukturen]] reiner P2P-Netzwerke durchbrechen, indem sie leistungsfähigere [[Knoten|Knoten]] (Super-Peers) für [[Koordination|Koordinationsaufgaben]] einsetzen, während schwächere Knoten (Weak-Peers) an diese angebunden sind.
- **Nutzen & Zweck:** Das Konzept löst [[Skalierbarkeitsproblem|Skalierbarkeitsprobleme]] und [[Performanzengpass|Performanzengpässe]] in [[unstrukturiert|unstrukturierten]] P2P-Netzwerken, indem es [[Suchanfrage|Suchanfragen]] und [[Ressourcenverwaltung|Ressourcenverwaltungen]] effizienter gestaltet. Super-Peers übernehmen [[Indexierung|Indexierungsaufgaben]] und [[Vermittlung|Vermittlungsfunktionen]], was die [[Netzlast|Netzlast]] reduziert.
- **Abgrenzung & Grenzen:** Super-Peer Netzwerke sind ungeeignet, wenn alle [[Knoten|Knoten]] ähnliche [[Leistungsfähigkeit|Leistungsfähigkeiten]] besitzen oder wenn [[Zentralisierung|Zentralisierungsrisiken]] (z. B. [[Ausfall|Ausfälle]] von Super-Peers) vermieden werden müssen. Im Vergleich zu [[rein dezentral|reindezentralen]] P2P-Systemen (z. B. [[Gnutella]]) oder [[strukturiert|strukturierten]] P2P-Netzwerken (z. B. [[Chord]]) führen sie eine [[Hierarchie|Hierarchie]] ein, die [[Komplexität|Komplexität]] erhöht. Alternativen wie [[Edge-Server Architekturen]] eignen sich besser für [[Content-Distribution|Content-Distribution]] mit klaren [[Server-Client-Beziehung|Server-Client-Beziehungen]].
- **Beispiel / Code:** Ein vereinfachtes Beispiel für die Interaktion in einem Super-Peer Netzwerk:

1. Ein Weak-Peer sendet eine Suchanfrage an seinen zugeordneten Super-Peer.
2. Der Super-Peer durchsucht seinen lokalen Index oder leitet die Anfrage an andere Super-Peers weiter.
3. Bei Erfolg wird die Antwort an den Weak-Peer zurückgegeben.

Pseudocode für einen Super-Peer:
```
class SuperPeer:
    def __init__(self):
        self.local_index = {}  # {resource_id: [weak_peer_ids]}
        self.connected_super_peers = []
        self.connected_weak_peers = []

    def handle_search_request(self, resource_id, requesting_peer):
        if resource_id in self.local_index:
            return self.local_index[resource_id]
        else:
            for super_peer in self.connected_super_peers:
                result = super_peer.handle_search_request(resource_id, self)
                if result:
                    return result
            return None
```
