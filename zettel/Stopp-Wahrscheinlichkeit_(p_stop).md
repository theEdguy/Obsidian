---
id: e299b69b-9edc-4eeb-ba55-8c43cfeb15ba
title: "Stopp-Wahrscheinlichkeit (p_stop)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - gossip-protokolle
  - netzwerk
  - skalierbarkeit
  - epidemische-algorithmen
  - kommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Stopp-Wahrscheinlichkeit (p_stop)]]

- **Kernkonzept:** Die Stopp-Wahrscheinlichkeit (p_stop) steuert in [[gossip-basiert|gossip-basierten]] [[Datenverbreitung|Datenverbreitungen]], wann ein [[Knoten]] die Weitergabe einer [[Aktualisierung]] mit einer bestimmten Wahrscheinlichkeit einstellt, um unnötige [[Kommunikation]] zu reduzieren.
- **Nutzen & Zweck:** Das Konzept löst das Problem der effizienten [[Skalierung]] in [[verteilte Systeme|verteilten Systemen]], indem es die Anzahl der [[Nachrichten]] begrenzt, sobald ein Großteil der [[Knoten]] die [[Aktualisierung]] bereits erhalten hat. Dadurch wird [[Netzwerk]]-Last reduziert, ohne die Verbreitung signifikant zu verzögern.
- **Abgrenzung & Grenzen:** p_stop sollte nicht verwendet werden, wenn eine garantierte Verbreitung der [[Aktualisierung]] an alle [[Knoten]] erforderlich ist, da mit steigendem p_stop die Wahrscheinlichkeit steigt, dass einige [[Knoten]] die [[Aktualisierung]] nie erhalten. Alternativen wie [[Anti-Entropy]] oder [[Push-Pull]]-Mechanismen bieten hier höhere Zuverlässigkeit, allerdings mit höherem [[Kommunikationsaufwand]].
- **Beispiel / Code:** Angenommen, ein [[Knoten]] verbreitet eine [[Aktualisierung]] via Gossip:
1. Der [[Knoten]] wählt zufällig einen anderen [[Knoten]] aus.
2. Falls der ausgewählte [[Knoten]] die [[Aktualisierung]] bereits kennt, stoppt der sendende [[Knoten]] mit Wahrscheinlichkeit p_stop = 0.2 die weitere Verbreitung.
3. Bei p_stop = 0.2 bleiben im Schnitt etwa 20% der [[Knoten]] ohne [[Aktualisierung]] (s ≈ 0.203 für N=10.000).
