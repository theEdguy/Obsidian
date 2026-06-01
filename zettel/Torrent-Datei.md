---
id: 59a84ac0-eef9-422e-9b48-436a97053a39
title: "Torrent-Datei"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - peer-to-peer
  - datenverteilung
  - metadaten
  - bittorrent
  - dezentralisierung
  - netzwerkprotokoll
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Torrent-Datei]]

- **Kernkonzept:** Eine [[Torrent-Datei]] ist eine Metadatei im [[BitTorrent-Protokoll]], die [[Information|Informationen]] über zu verteilende [[Daten]] enthält, darunter [[Hash-Wert|Hash-Werte]] der [[Datei|Dateien]] und die [[Adresse]] des [[Tracker|Trackers]], der den [[Schwarm]] der [[Peer|Peers]] koordiniert.
- **Nutzen & Zweck:** Die [[Torrent-Datei]] löst das [[Problem]] der effizienten und dezentralen Verteilung großer [[Daten|Datensätze]] in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], indem sie [[Metadaten]] bereitstellt, die es [[Knoten]] ermöglichen, sich mit anderen [[Peer|Peers]] zu verbinden und [[Daten|Datenfragmente]] auszutauschen, ohne auf einen zentralen [[Server]] angewiesen zu sein.
- **Abgrenzung & Grenzen:** Eine [[Torrent-Datei]] sollte nicht genutzt werden, wenn [[Daten]] klein sind oder eine zentrale [[Verteilung]] ausreicht, da der [[Overhead]] der [[Koordination]] und [[Fragmentierung]] den [[Nutzen]] überwiegt. Im Vergleich zu [[Client-Server-Architektur|Client-Server-Architekturen]] fehlt eine zentrale [[Kontrolle]], was zu [[Sicherheitsrisiko|Sicherheitsrisiken]] (z. B. [[Malware]]) oder unzuverlässigen [[Quelle|Quellen]] führen kann. Alternativen wie [[Content Delivery Network|CDNs]] oder [[Super-Peer-Netzwerk|Super-Peer-Netzwerke]] bieten mehr [[Kontrolle]] und [[Performanz]] für bestimmte [[Anwendungsfall|Anwendungsfälle]].
- **Beispiel / Code:** Eine typische [[Torrent-Datei]] im [[Bencode-Format]] (ein einfaches [[Datenformat]] für [[Metadaten]]) sieht wie folgt aus:
```
d8:announce35:http://tracker.example.com/announce
4:infod6:lengthi123456789e4:name12:example.txt
12:piece lengthi16384e6:pieces20:...<20-byte SHA1 hash>...
e
```
Hierbei enthält die Datei:
- Die [[URL]] des [[Tracker|Trackers]] (`announce`).
- [[Metadaten]] über die [[Datei]] (`info`), inkl. [[Name]], [[Größe]] (`length`) und [[Hash-Wert|Hash-Werte]] der [[Datenfragment|Datenfragmente]] (`pieces`).
