---
id: 6d6b048a-2674-49df-baa8-c9690d52308b
title: "Application-Level Multicasting (ALM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - netzwerk
  - multicast
  - overlay-netzwerke
  - p2p
  - routing
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Application-Level Multicasting (ALM)]]

- **Kernkonzept:** Application-Level Multicasting (ALM) organisiert [[Knoten|Knoten]] eines verteilten [[System|Systems]] als Overlay-Netzwerk, um [[Daten|Daten]] effizient zu verbreiten – typischerweise als [[Baum|Baum]] oder [[Mesh-Netzwerk|Mesh-Netzwerk]] – ohne Unterstützung der Netzwerkschicht.
- **Nutzen & Zweck:** ALM löst das [[Problem]] der skalierbaren [[Datenverteilung|Datenverteilung]] in verteilten [[System|Systemen]], wo IP-Multicast nicht verfügbar oder unpraktikabel ist. Es ermöglicht flexible, anwendungsspezifische [[Multicast-Routing|Multicast-Routingstrategien]] und reduziert die Abhängigkeit von Netzwerkinfrastruktur.
- **Abgrenzung & Grenzen:** ALM sollte nicht genutzt werden, wenn niedrige Latenz oder minimale Netzwerkbelastung kritisch sind, da es höhere [[Link-Stress|Link-Stress]]- und [[Stretch-Werte|Stretch-Werte]] als IP-Multicast verursacht. Alternativen wie [[Message-Queuing-Systeme|Message-Queuing-Systeme]] (z. B. IBM MQ) oder [[Gossip-Protokolle|Gossip-Protokolle]] eignen sich besser für asynchrone, fehlertolerante Kommunikation.
- **Beispiel / Code:** Beispiel: Baum-basiertes ALM in Chord (P2P-Ring):
1. Initiator generiert Multicast-ID `mid` und sucht `succ(mid)` (Wurzelknoten).
2. Knoten `P` sendet Beitrittsanfrage zur Wurzel.
3. Knoten `Q` auf dem Pfad wird zum Elternknoten von `P`, falls `Q` noch keinen Baum kennt.
4. Der Baum wächst dynamisch durch Beitrittsanfragen, ohne zentrale Steuerung.
