---
id: 96d8b744-e11e-4531-8028-e03f369445c1
title: "Garbage Collection in verteilten Systemen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteiltes-system
  - datenmanagement
  - konsistenz
  - gossip-protokoll
  - garbage-collection
  - koordination
  - epidemische-algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Garbage Collection in verteilten Systemen]]

- **Kernkonzept:** Garbage Collection in [[verteiltes System|verteilten Systemen]] verwaltet das sichere Löschen nicht mehr benötigter [[Datenobjekt|Datenobjekte]] oder [[Metadatum|Metadaten]] wie [[Totenschein|Totenscheine]], ohne die Konsistenz des Systems zu gefährden. Es nutzt [[epidemischer Algorithmus|epidemische Algorithmen]] und globale Koordination, um Löschoperationen zuverlässig zu verbreiten.
- **Nutzen & Zweck:** Das Konzept löst das [[Fundamentalproblem|Fundamentalproblem]] des sicheren Löschens in [[verteiltes System|verteilten Systemen]], wo einfache Löschungen durch [[Datenverbreitung|Datenverbreitungsmechanismen]] wie Gossiping rückgängig gemacht werden. Es stellt sicher, dass [[Datenobjekt|Datenobjekte]] nach ihrer Nutzungsdauer entfernt werden, ohne die [[Systemkonsistenz]] zu beeinträchtigen.
- **Abgrenzung & Grenzen:** Garbage Collection in [[verteiltes System|verteilten Systemen]] ist nicht geeignet für Szenarien mit extrem hoher [[Dynamik]] (z. B. häufige Knotenausfälle) oder wenn die [[Latenz]] der globalen Koordination inakzeptabel ist. Alternativen wie [[Lease-basierte Mechanismen]] oder [[manuelle Verwaltung]] können in solchen Fällen effizienter sein. Im Gegensatz zu lokaler Garbage Collection erfordert es zusätzliche [[Kommunikationsaufwand|Kommunikationsaufwände]] und [[Synchronisationsmechanismus|Synchronisationsmechanismen]].
- **Beispiel / Code:** Ein Beispiel für die Implementierung eines Totenscheins in einem Gossip-basierten System:

1. Ein Knoten initiiert das Löschen eines [[Datenobjekt|Datenobjekts]] und erzeugt einen Totenschein mit einer eindeutigen ID und einer maximalen Lebensdauer (TTL).
2. Der Totenschein wird via Push-Pull-Gossiping an andere Knoten verbreitet.
3. Nach Ablauf der TTL wird ein globaler Algorithmus ausgeführt, um zu prüfen, ob alle Knoten den Totenschein erhalten haben.
4. Falls ja, wird der Totenschein und das [[Datenobjekt]] endgültig gelöscht; andernfalls wird die TTL verlängert.

Pseudocode:
```
procedure initiateDeletion(dataId):
    tombstone = createTombstone(dataId, ttl=1000)
    gossipProtocol.broadcast(tombstone, mode=PUSH_PULL)

procedure checkTombstoneExpiry():
    if allNodesAcknowledge(tombstone.id):
        deleteTombstone(tombstone.id)
        deleteData(dataId)
    else:
        tombstone.ttl *= 2
        gossipProtocol.rebroadcast(tombstone)
```
