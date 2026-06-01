---
id: 78f7bb47-8ac9-4d60-9de8-18f6562846c6
title: "Gossip-basierte Datenverbreitung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - epidemische_algorithmen
  - datenverbreitung
  - skalierbarkeit
  - fehlertoleranz
  - netzwerkprotokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Gossip-basierte Datenverbreitung]]

- **Kernkonzept:** Ein [[epidemischer Algorithmus|epidemische Algorithmen]] zur dezentralen Verbreitung von [[Aktualisierung|Aktualisierungen]] in [[verteiltes System|verteilten Systemen]], bei dem [[Knoten]] zufällig Informationen austauschen, ähnlich wie Gerüchte in sozialen Netzwerken.
- **Nutzen & Zweck:** Löst das [[Problem]] der skalierbaren und fehlertoleranten Datenverbreitung in großen [[Netzwerk|Netzwerken]], ohne zentrale Steuerung oder komplexe [[Koordination]]. Ideal für [[Systeme]] mit hoher [[Knoten]]-Dynamik oder unzuverlässigen Verbindungen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn garantierte Konsistenz oder sofortige Verbreitung erforderlich ist. Unterscheidet sich von [[deterministischen Protokoll|deterministischen Protokollen]] (z. B. [[Multicast]]) durch probabilistische Verbreitung und höhere [[Latenz]]. Bei kritischen Löschoperationen sind zusätzliche Mechanismen (z. B. [[Totenschein|Totenscheine]]) nötig.
- **Beispiel / Code:** Pseudocode für Push-Pull-Gossip:

function gossipPushPull():
    Q = randomNode()
    myUpdates = getLocalUpdates()
    Q_updates = sendReceive(Q, myUpdates)
    mergeUpdates(Q_updates)

// Nach O(log(N)) Runden sind alle Knoten synchronisiert.
