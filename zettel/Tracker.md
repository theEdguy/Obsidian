---
id: 69e6d4a3-6dfc-47f7-8abc-8a6e446897c7
title: "Tracker"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - koordination
  - peer-to-peer
  - hybrid
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Tracker]]

- **Kernkonzept:** Ein [[Tracker]] ist ein zentraler [[Server|Server]], der in [[hybride Architekturen|hybriden Architekturen]] wie [[BitTorrent]] die [[Koordination]] aktiver [[Knoten]] übernimmt, indem er eine Liste von [[Peer|Peers]] verwaltet, die Teile einer [[Datei]] besitzen.
- **Nutzen & Zweck:** Der [[Tracker]] löst das [[Problem]] der effizienten [[Verteilung]] und [[Suche]] von [[Ressourcen]] in [[Peer-to-Peer-Systemen|Peer-to-Peer-Systemen]], indem er [[Knoten]] dynamisch verbindet und so die [[Skalierbarkeit]] und [[Performanz]] verbessert. Ohne ihn müssten [[Peer|Peers]] aufwendige [[Flooding]]- oder [[Random-Walk-Algorithmen]] nutzen.
- **Abgrenzung & Grenzen:** Ein [[Tracker]] sollte nicht in [[rein dezentralisierten Systemen|rein dezentralisierten Systemen]] eingesetzt werden, da er einen [[Single Point of Failure]] darstellt und die [[Symmetrie]] des [[Netzwerks]] bricht. Alternativen wie [[Super-Peer-Netzwerke]] oder [[verteilte Hash-Tabellen]] (DHT) sind robuster, aber komplexer in der [[Implementierung]].
- **Beispiel / Code:** Ein [[Tracker]] in [[BitTorrent]] antwortet auf HTTP-Anfragen mit einer Liste aktiver [[Peer|Peers]]:
```
GET /announce?info_hash=...&peer_id=...&port=... HTTP/1.1
Host: tracker.example.com

HTTP/1.1 200 OK
Content-Type: text/plain

192.168.1.10:6881
10.0.0.5:6889
```
