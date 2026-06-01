---
id: fab6e5e7-bd4b-4fb9-b420-b15f32d3490b
title: "Baum-basiertes Multicasting auf Anwendungsebene"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - multicast
  - overlay_netzwerke
  - algorithmen
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Baum-basiertes Multicasting auf Anwendungsebene]]

- **Kernkonzept:** Baum-basiertes Multicasting auf Anwendungsebene organisiert [[Knoten|Knoten]] eines verteilten [[System|Systems]] in einem [[Overlay-Netzwerk|Overlay-Netz]] als Baumstruktur, um [[Daten|Daten]] effizient an mehrere [[Empfänger|Empfänger]] zu verbreiten, ohne auf Netzwerkschicht-Multicast angewiesen zu sein.
- **Nutzen & Zweck:** Es löst das Problem der skalierbaren [[Datenverteilung|Datenverteilung]] in verteilten [[System|Systemen]], wo Netzwerkschicht-Multicast nicht verfügbar oder ineffizient ist. Durch die Nutzung eines Baums als [[Overlay-Netzwerk|Overlay-Netz]] wird sichergestellt, dass [[Nachrichten|Nachrichten]] ohne Redundanz und mit minimalem [[Overhead|Overhead]] verbreitet werden.
- **Abgrenzung & Grenzen:** Nicht geeignet für hochdynamische [[Netzwerk|Netzwerke]] mit häufigen [[Knotenausfällen|Knotenausfällen]], da die Baumstruktur instabil werden kann. Im Vergleich zu [[Mesh-basierten|Mesh-basierten]] oder [[Gossip-Protokollen|Gossip-Protokollen]] bietet es weniger [[Fehlertoleranz|Fehlertoleranz]], ist aber effizienter in Bezug auf [[Bandbreitennutzung|Bandbreitennutzung]] und [[Latenz|Latenz]]. Alternativen wie Flooding oder Gossiping sind robuster, aber weniger effizient.
- **Beispiel / Code:** Beispiel für die Konstruktion eines Multicast-Baums in Chord (Pseudocode):

1. Initiator generiert einen Multicast-Bezeichner `mid`.
2. Suche `succ(mid)` (den für `mid` zuständigen Knoten), der zur Wurzel des Baums wird.
3. Ein neuer Knoten `P` sendet einen Beitritts-Request zur Wurzel.
4. Auf dem Pfad zur Wurzel:
   - Falls ein Knoten `Q` den Request noch nicht kennt, wird `Q` zum Elternknoten von `P` und leitet den Request weiter.
   - Falls `Q` den Baum bereits kennt, wird `P` direkt als Kind von `Q` eingefügt.

Dies stellt sicher, dass jeder Knoten genau einen Elternknoten hat und der Baum effizient aufgebaut wird.
