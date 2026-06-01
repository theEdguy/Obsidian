---
id: 59ac4e5f-a32e-430a-a6d9-aaabaf7b4a38
title: "Stretch (ALM-Metrik)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - netzwerk
  - multicast
  - leistung
  - overlay-netzwerke
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Stretch (ALM-Metrik)]]

- **Kernkonzept:** Die [[Stretch|Stretch]]-Metrik misst das Verhältnis der [[Verzögerung|Verzögerungen]] eines Pfades im [[Application-Level Multicasting|Application-Level-Multicast]]-Overlay-Netzwerk zur direkten [[Verzögerung|Verzögerung]] auf Netzwerkebene. Sie quantifiziert die [[Effizienz|Ineffizienz]] des Overlay-Pfades im Vergleich zum optimalen physischen Pfad.
- **Nutzen & Zweck:** Die [[Stretch|Stretch]]-Metrik dient zur Bewertung der [[Leistung|Leistungsfähigkeit]] von [[Application-Level Multicasting|ALM]]-Protokollen. Sie hilft, [[Overlay-Netzwerk|Overlay-Netzwerke]] zu optimieren, indem sie [[Pfad|Pfade]] identifiziert, die im Vergleich zur direkten Netzwerkkommunikation unnötig lange [[Verzögerung|Verzögerungen]] verursachen.
- **Abgrenzung & Grenzen:** Die [[Stretch|Stretch]]-Metrik sollte nicht isoliert betrachtet werden, da sie nur die [[Verzögerung|Verzögerung]] misst und andere Faktoren wie [[Link Stress]] oder [[Bandbreite]] ignoriert. Sie ist ungeeignet für [[Flooding]]- oder [[Gossip-basierte Datenverbreitung|Gossip-basierte]] Protokolle, die keine klaren Pfadstrukturen aufweisen. Alternativen wie [[Link Stress]] fokussieren sich auf die Belastung physischer [[Netzwerk|Netzwerk]]-Links.
- **Beispiel / Code:** Gegeben sei ein Overlay-Pfad von Knoten B zu Knoten C mit einer ALM-Verzögerung von 73 Einheiten und einer direkten Netzwerkverzögerung von 47 Einheiten. Die Stretch berechnet sich als:

Stretch = ALM-Verzögerung / Netzwerkverzögerung
Stretch = 73 / 47 ≈ 1,55

Dies bedeutet, dass der Overlay-Pfad etwa 55 % länger ist als der optimale physische Pfad.
