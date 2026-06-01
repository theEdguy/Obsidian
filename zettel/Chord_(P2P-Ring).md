---
id: a443f91e-535e-4bb1-bad8-302b4163203d
title: "Chord (P2P-Ring)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - peer-to-peer
  - hashing
  - netzwerk_topologie
  - skalierbarkeit
  - algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Chord (P2P-Ring)]]

- **Kernkonzept:** Chord ist ein [[Algorithmus|Algorithmen]] für verteilte [[Hash-Tabelle|Hash-Tabellen]] in [[Peer-to-Peer|Peer-to-Peer-Netzwerken]], der Knoten in einem [[Ring|Ringstruktur]] organisiert und effiziente [[Suche|Suchoperationen]] mittels [[Finger-Tabelle|Finger-Tabellen]] ermöglicht.
- **Nutzen & Zweck:** Chord löst das [[Problem]] der skalierbaren und dezentralen [[Ressourcenverwaltung]] in großen [[Netzwerk|Netzwerken]], indem es eine strukturierte [[Topologie]] mit logarithmischer [[Komplexität]] für [[Schlüssel|Schlüsselzugriffe]] bereitstellt. Es ermöglicht robuste [[Datenverteilung]] und [[Fehlertoleranz]] ohne zentrale [[Kontrolle]].
- **Abgrenzung & Grenzen:** Chord eignet sich nicht für [[Anwendung|Anwendungen]], die starke [[Konsistenz]] oder [[Echtzeitgarantien]] benötigen. Im Vergleich zu unstrukturierten [[Netzwerk|Netzwerken]] (z. B. [[Gnutella]]) erfordert es höhere [[Aufwand|Aufwände]] für die [[Wartung]] der [[Ringstruktur]]. Für [[Multicast|Multicast-Kommunikation]] sind zusätzliche [[Mechanismus|Mechanismen]] (z. B. [[Baumkonstruktion]]) nötig.
- **Beispiel / Code:** ```python
# Pseudocode: Suche nach einem Schlüssel in Chord
class ChordNode:
    def find_successor(self, key):
        if self.id < key <= self.successor.id:
            return self.successor
        else:
            # Nutze Finger-Tabelle für effiziente Suche
            closest = self.closest_preceding_node(key)
            return closest.find_successor(key)
```

*Erläuterung*: Jeder Knoten leitet die [[Suche]] an den nächsten bekannten Knoten in seiner [[Finger-Tabelle]] weiter, bis der zuständige Knoten gefunden ist.
