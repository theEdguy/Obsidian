---
id: 4474719d-23e6-4460-8243-ace9b1eecbc3
title: "Peer-to-Peer (P2P) Architekturen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - netzwerk-architektur
  - dezentralisierung
  - datenverteilung
  - routing
  - skalierbarkeit
  - chord
  - p2p
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Peer-to-Peer (P2P) Architekturen]]

- **Kernkonzept:** Peer-to-Peer (P2P) [[Architektur|Architekturen]] sind dezentrale [[System|Systeme]], in denen alle [[Prozess|Prozesse]] gleichberechtigt agieren und sowohl [[Client|Clients]] als auch [[Server|Server]] (sog. Servants) sein können, um [[Ressource|Ressourcen]] und [[Dienst|Dienste]] direkt untereinander zu teilen.
- **Nutzen & Zweck:** P2P-[[Architektur|Architekturen]] lösen das Problem der [[Skalierbarkeit]] und [[Einzelpunktausfall|Einzelpunktausfälle]] in zentralisierten [[System|Systemen]], indem sie [[Lastverteilung|Lasten]] und [[Verantwortung|Verantwortungen]] auf alle [[Knoten|Knoten]] verteilen. Sie ermöglichen effiziente [[Datenverteilung|Datenverteilungen]] und [[Ressourcennutzung|Ressourcennutzungen]] ohne zentrale [[Koordination|Koordination]].
- **Abgrenzung & Grenzen:** P2P-[[Architektur|Architekturen]] sind ungeeignet für [[Anwendung|Anwendungen]], die starke [[Konsistenz]] oder zentrale [[Kontrolle]] erfordern, wie z. B. [[Transaktionssystem|Transaktionssysteme]] oder [[Sicherheitskritische Systeme|sicherheitskritische Systeme]]. Im Vergleich zu [[Client-Server-Architektur|Client-Server-Architekturen]] sind sie komplexer in der [[Implementierung]] und [[Wartung]], bieten aber bessere [[Skalierbarkeit]] und [[Ausfallsicherheit]]. Strukturierte P2P-[[Systeme]] (z. B. Chord) erfordern zusätzliche [[Mechanismus|Mechanismen]] für [[Routing]] und [[Datenplatzierung|Datenplatzierungen]].
- **Beispiel / Code:** Beispiel für ein strukturiertes P2P-System (Chord-Ring):

1. Knoten und Daten werden durch eine Hash-Funktion (z. B. SHA-1) auf einen m-Bit-Schlüsselraum abgebildet.
2. Jeder Knoten verwaltet einen Bereich des Schlüsselraums und speichert die zugehörigen (Schlüssel, Wert)-Paare.
3. Lookup-Operation:
   - Gesucht wird der Knoten, der den Schlüssel `k` speichert (Successor von `k`).
   - Beispiel: `lookup(3)@9` im Chord-Ring:
     - Knoten 9 leitet die Anfrage an Knoten 28 weiter (nächster Finger-Eintrag).
     - Knoten 28 leitet an Knoten 1 weiter.
     - Knoten 1 leitet an Knoten 4 weiter (Successor von Schlüssel 3).

Pseudocode für Chord-Lookup:
```
def find_successor(k, node):
    if k ∈ (node.id, node.successor.id]:
        return node.successor
    else:
        n0 = node.closest_preceding_node(k)
        return find_successor(k, n0)
```
