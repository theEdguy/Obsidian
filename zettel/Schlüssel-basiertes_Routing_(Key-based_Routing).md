---
id: b702a402-1943-4eb1-87e7-c6819398c06b
title: "Schlüssel-basiertes Routing (Key-based Routing)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - peer-to-peer
  - routing
  - datenverteilung
  - skalierbarkeit
  - hashing
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Schlüssel-basiertes Routing (Key-based Routing)]]

- **Kernkonzept:** Schlüssel-basiertes Routing ermöglicht die effiziente Verteilung und [[Abfrage|Abfragen]] von [[Datenelement|Datenelementen]] in [[dezentralisiert|dezentralisierten]] [[System|Systemen]], indem jedem [[Datenelement]] ein eindeutiger [[Schlüssel]] zugeordnet wird, der das Routing zu einem verantwortlichen [[Knoten]] steuert.
- **Nutzen & Zweck:** Es löst das [[Problem]] der skalierbaren und deterministischen [[Datenverteilung]] in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], indem es [[Anfrage|Anfragen]] ohne zentrale [[Koordination]] direkt zum zuständigen [[Knoten]] leitet. Dies reduziert [[Latenz]] und vermeidet [[Engpässe]] in [[verteilten Systemen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Systeme]], die komplexe [[Abfrage|Abfragen]] (z. B. Bereichsabfragen) oder häufige [[Datenmigration|Datenmigrationen]] erfordern. Im Vergleich zu [[zentralisiert|zentralisierten]] [[Lösungen]] wie [[Datenbank|Datenbanken]] fehlt die Unterstützung für [[Transaktion|Transaktionen]] oder [[ACID-Eigenschaft|ACID-Eigenschaften]]. Alternativen wie [[Flooding]] oder [[verzeichnisbasiert|Verzeichnisdienste]] bieten mehr Flexibilität, aber geringere Skalierbarkeit.
- **Beispiel / Code:** Beispiel: Chord-Ring (vereinfacht)

1. Jeder Knoten erhält einen m-Bit-Bezeichner (z. B. durch Hashing seiner IP-Adresse).
2. Ein Datenelement mit Schlüssel k wird im Knoten gespeichert, dessen Bezeichner der kleinste ≥ k ist (Successor).
3. Routing-Beispiel:
   - Knoten 9 sucht Schlüssel 3.
   - Abkürzungen (Finger-Tabelle) leiten die Anfrage über Knoten 28 → 1 → 4 (Successor von 3).

Pseudocode für Lookup:
```
def lookup(key, node):
    if node.successor.id >= key:
        return node.successor
    else:
        next_node = node.closest_preceding_node(key)
        return lookup(key, next_node)
```
