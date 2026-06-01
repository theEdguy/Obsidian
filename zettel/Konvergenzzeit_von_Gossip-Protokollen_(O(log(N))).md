---
id: a1799e1e-0ec0-4816-9094-83085182c510
title: "Konvergenzzeit von Gossip-Protokollen (O(log(N)))"
date: 2026-06-01
tags:
  - verteilte_systeme
  - gossip_protokolle
  - skalierbarkeit
  - netzwerk
  - algorithmen
  - konvergenz
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Konvergenzzeit von Gossip-Protokollen (O(log(N)))]]

- **Kernkonzept:** Die Konvergenzzeit von [[Gossip-Protokoll|Gossip-Protokollen]] beschreibt, wie schnell sich [[Aktualisierung|Aktualisierungen]] in einem verteilten [[System|System]] ausbreiten. Beim [[Push-Pull-Verfahren|Push-Pull-Verfahren]] wird eine Zeitkomplexität von O(log(N)) Runden benötigt, um alle N [[Knoten]] zu erreichen.
- **Nutzen & Zweck:** Dieses Konzept ermöglicht effiziente und skalierbare [[Datenverbreitung]] in großen verteilten [[System|Systemen]], ohne zentrale [[Koordination]]. Es löst das Problem der schnellen Informationsverteilung bei minimalem [[Netzwerk]]-Overhead und hoher [[Fehlertoleranz]].
- **Abgrenzung & Grenzen:** Gossip-Protokolle sind ungeeignet, wenn eine garantierte [[Zustellung]] oder strikte [[Konsistenz]] erforderlich ist. Alternativen wie [[Broadcast]] oder [[Tree-basierte Protokolle]] bieten deterministische Ergebnisse, skalieren aber schlechter. Zudem ist die Konvergenzzeit probabilistisch und hängt von der zufälligen [[Knotenauswahl]] ab.
- **Beispiel / Code:** // Pseudocode für ein Push-Pull-Gossip-Protokoll
function gossipRound() {
    Q = randomNode(); // Wähle zufälligen Knoten Q
    if (pushPullMode) {
        sendUpdatesTo(Q); // Sende eigene Aktualisierungen
        receiveUpdatesFrom(Q); // Empfange Aktualisierungen von Q
    }
    // Nach O(log(N)) Runden sind alle Knoten aktualisiert
}
