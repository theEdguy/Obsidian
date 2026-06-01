---
id: c18696b0-fdac-4044-aecc-0ea67cb7b848
title: "BitTorrent"
date: 2026-06-01
tags:
  - verteilte_systeme
  - peer-to-peer
  - dateiübertragung
  - dezentralisierung
  - netzwerkprotokoll
  - verteilte-systeme
  - hybride-architektur
  - koordination
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[BitTorrent]]

- **Kernkonzept:** BitTorrent ist ein [[Protokoll|Protokolle]] für [[dezentral|dezentrale]] [[Dateiübertragung|Dateiübertragungen]] in [[Peer-to-Peer|Peer-to-Peer-Netzwerken]], bei dem [[Teilnehmer|Teilnehmer]] (Peers) [[Dateifragment|Dateifragmente]] untereinander austauschen, statt sie von einem zentralen [[Server]] zu beziehen.
- **Nutzen & Zweck:** Es löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] zentraler [[Server]] bei der Verteilung großer [[Datei|Dateien]], indem es die [[Bandbreite]] und [[Ressource|Ressourcen]] aller [[Teilnehmer]] nutzt. Dadurch wird die [[Last]] verteilt und die [[Verfügbarkeit]] erhöht, besonders bei hoher [[Nachfrage]].
- **Abgrenzung & Grenzen:** BitTorrent eignet sich nicht für [[Echtzeitdaten]] oder kleine [[Datei|Dateien]], da der [[Overhead]] durch [[Tracker]] und [[Metadaten]] (Torrent-Dateien) zu groß ist. Im Vergleich zu [[strukturierten P2P-Systemen]] wie [[DHT]] fehlt eine effiziente [[Suchfunktion]], und im Gegensatz zu [[Client-Server-Architekturen]] ist die [[Downloadgeschwindigkeit]] abhängig von der [[Kooperation]] der Peers. Nicht geeignet für [[privatsphärenkritische]] Anwendungen, da [[IP-Adressen]] der Peers sichtbar sind.
- **Beispiel / Code:** Eine Torrent-Datei enthält Metadaten wie:
```
{
  "announce": "http://tracker.example.com/announce",
  "info": {
    "name": "beispiel.iso",
    "piece length": 262144,
    "pieces": "<SHA-1-Hashes der Fragmente>",
    "length": 1073741824
  }
}
```
Ein Peer lädt Fragmente von anderen Peers herunter und teilt bereits erhaltene Fragmente im [[Schwarm]] (Swarm). Der [[Tracker]] koordiniert die [[Verbindung|Verbindungen]] zwischen den Peers.
