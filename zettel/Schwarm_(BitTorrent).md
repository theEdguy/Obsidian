---
id: 3d26b4d5-1b96-43ce-9678-3290ac9c256c
title: "Schwarm (BitTorrent)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - peer-to-peer
  - verteilte-systeme
  - dateitransfer
  - netzwerk
  - dezentralisierung
  - koordination
  - bittorrent
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Schwarm (BitTorrent)]]

- **Kernkonzept:** Ein [[Schwarm|Schwarm]] in [[BitTorrent]] bezeichnet eine dynamische Gruppe von [[Peer|Peers]], die gemeinsam eine Datei oder Teile davon herunterladen und gleichzeitig untereinander austauschen, um die [[Verfügbarkeit]] und [[Download-Geschwindigkeit]] zu erhöhen.
- **Nutzen & Zweck:** Der [[Schwarm]] löst das Problem der [[Skalierbarkeit]] und [[Lastverteilung]] in [[Peer-to-Peer]]-Netzwerken, indem er [[Ressourcen]] dezentral nutzt und [[Engpässe]] bei einzelnen [[Knoten]] vermeidet. Dadurch wird die [[Effizienz]] des [[Dateitransfers]] gesteigert, ohne auf zentrale [[Server]] angewiesen zu sein.
- **Abgrenzung & Grenzen:** Ein [[Schwarm]] eignet sich nicht für [[Echtzeit-Anwendungen]] mit strengen [[Latenz-Anforderungen]], da die [[Datenverteilung]] von der [[Verfügbarkeit]] und [[Kooperation]] der [[Peer|Peers]] abhängt. Im Vergleich zu [[Super-Peer]]-Netzwerken oder [[Client-Server]]-Architekturen fehlt eine zentrale [[Kontrolle]], was zu [[Inkonsistenzen]] oder [[Sicherheitsrisiken]] führen kann. Für kleine Dateien oder [[Einzelabrufe]] ist der [[Overhead]] der [[Schwarm-Bildung]] oft unnötig.
- **Beispiel / Code:** Eine Torrent-Datei (z. B. `beispiel.torrent`) enthält Metadaten wie Dateinamen, Hash-Werte der Dateiteile und die Adresse eines [[Tracker|Trackers]]. Ein [[Peer]] tritt dem [[Schwarm]] bei, indem er:
1. Die Torrent-Datei von einer [[Webseite]] lädt.
2. Den [[Tracker]] kontaktiert, um eine Liste aktiver [[Peer|Peers]] zu erhalten.
3. Dateiteile von mehreren [[Peer|Peers]] parallel herunterlädt und gleichzeitig bereits erhaltene Teile an andere [[Peer|Peers]] weitergibt.

Beispiel für eine vereinfachte Tracker-Antwort (JSON-ähnlich):
```
{
  "peers": [
    {"ip": "192.168.1.10", "port": 6881},
    {"ip": "10.0.0.5", "port": 6882}
  ]
}
```
