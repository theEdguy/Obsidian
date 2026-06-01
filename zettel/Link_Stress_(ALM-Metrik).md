---
id: c13e4059-624c-4e6e-a62f-194e46e85802
title: "Link Stress (ALM-Metrik)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - multicast
  - overlay-netzwerke
  - performance-metriken
  - verteilte-systeme
  - routing
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Link Stress (ALM-Metrik)]]

- **Kernkonzept:** Der [[Link Stress|Link-Stress]] misst, wie oft eine Nachricht desselben [[Multicast|Multicasts]] denselben physischen [[Netzwerk|Netzwerk]]-Link in einem [[Application-Level Multicasting|Application-Level-Multicast]]-Overlay passiert. Er quantifiziert die redundante Belastung eines Links durch identische Nachrichten.
- **Nutzen & Zweck:** Der [[Link Stress|Link-Stress]] dient zur Bewertung der Effizienz von [[Overlay-Netzwerk|Overlay-Netzwerken]] in [[Verteilte Systeme|verteilten Systemen]]. Er hilft, Engpässe und ineffiziente Routing-Pfade zu identifizieren, um die [[Skalierbarkeit]] und [[Performance]] von [[Multicast|Multicast]]-Kommunikation zu optimieren.
- **Abgrenzung & Grenzen:** Der [[Link Stress|Link-Stress]] ist nicht relevant für [[Unicast]]- oder [[Broadcast]]-Kommunikation, da diese keine redundanten Pfade im Overlay nutzen. Alternativen wie [[Stretch]] oder [[Knotengrad]] messen andere Aspekte der Overlay-Effizienz. Bei [[IP-Multicast]] entfällt die Metrik, da das Routing auf Netzwerkebene optimiert wird.
- **Beispiel / Code:** Im Beispiel-Slide (Folie 43) wird eine Nachricht von Knoten A zu Knoten D gesendet. Der physische Link zwischen Router Ra und Rb wird zweimal durchlaufen (einmal für A→B, einmal für A→D), was zu einem [[Link Stress|Link-Stress]] von 2 führt. Dies zeigt eine ineffiziente Overlay-Struktur an.
