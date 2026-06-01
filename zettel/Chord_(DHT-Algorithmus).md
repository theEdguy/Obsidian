---
id: 3d781d9f-7e47-4722-a628-487f7b105c8f
title: "Chord (DHT-Algorithmus)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - dht
  - namensauflösung
  - peer-to-peer
  - algorithmus
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Chord (DHT-Algorithmus)]]

- **Kernkonzept:** Chord ist ein [[Algorithmus|Algorithmen]] für [[Verteilte_Hash-Tabelle|Verteilte Hash-Tabellen]] (DHTs), der [[Knoten|Knoten]] in einem [[logischer_Ring|logischen Ring]] organisiert, um die [[Namensauflösung|Auflösung]] von [[Bezeichner|Bezeichnern]] in [[verteilte_Systeme|verteilten Systemen]] effizient zu ermöglichen.
- **Nutzen & Zweck:** Chord löst das [[Problem]] der [[Skalierbarkeit]] und [[Effizienz]] bei der [[Suche]] nach [[Entität|Entitäten]] in großen [[Peer-to-Peer-Netzwerk|Peer-to-Peer-Netzwerken]], indem es die [[Lastverteilung]] und [[Lokalisierung]] von [[Schlüssel|Schlüsseln]] in logarithmischer Zeit ermöglicht. Es vermeidet zentrale [[Namensdienst|Namensdienste]] und [[Broadcasting]]-Ansätze, die nicht skalieren.
- **Abgrenzung & Grenzen:** Chord eignet sich nicht für [[Systeme]] mit häufigen [[Knotenausfall|Knotenausfällen]] oder stark dynamischen [[Topologie|Topologien]], da die [[Finger-Tabelle|Finger-Tabellen]] regelmäßig aktualisiert werden müssen. Alternativen wie [[Hierarchical_Location_Service|hierarchische Ansätze]] (z. B. DNS) oder [[Heimatbasierte_Ansätze]] sind besser für [[geografische_Skalierbarkeit|geografisch verteilte]] oder mobile [[Entität|Entitäten]] geeignet.
- **Beispiel / Code:** Ein Knoten mit ID 1 sucht den Schlüssel 26 in einem Chord-Ring mit m=5 Bit:
1. Finger-Tabelle von Knoten 1:
   FT1[1] = succ(1 + 2^0) = succ(2) = 3
   FT1[2] = succ(1 + 2^1) = succ(3) = 9
   FT1[3] = succ(1 + 2^2) = succ(5) = 9
   FT1[4] = succ(1 + 2^3) = succ(9) = 18
   FT1[5] = succ(1 + 2^4) = succ(17) = 20
2. Suche nach 26: Knoten 1 leitet die Anfrage an Knoten 20 weiter (da 20 ≤ 26 < 30).
3. Knoten 20 leitet die Anfrage an Knoten 28 weiter (FT20[1] = 28).
4. Knoten 28 erkennt, dass 26 in seinen Zuständigkeitsbereich fällt (28 ≥ 26) und gibt die Adresse zurück.
