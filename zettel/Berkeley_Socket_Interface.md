---
id: 7c8ad05b-f8dc-4f69-ab45-859d0e39bf21
title: "Berkeley Socket Interface"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - interprozesskommunikation
  - socket-programmierung
  - client-server
  - verteilte-systeme
  - low-level-kommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Berkeley Socket Interface]]

- **Kernkonzept:** Das Berkeley Socket Interface ist eine standardisierte Programmierschnittstelle zur [[Kommunikation|Kommunikations]]-steuerung in [[Netzwerk|Netzwerken]], die das Senden und Empfangen von [[Nachricht|Nachrichten]] zwischen [[Prozess|Prozessen]] auf verschiedenen [[Rechner|Rechnern]] ermöglicht.
- **Nutzen & Zweck:** Es löst das [[Problem]] der [[Interprozesskommunikation]] über [[Netzwerk|Netzwerkgrenzen]] hinweg, indem es eine einheitliche und portable [[Schnittstelle]] für [[transiente]] und [[persistente]] [[Verbindung|Verbindungen]] bereitstellt. Damit ermöglicht es die Entwicklung [[verteilter Systeme]] mit [[Client-Server-Architektur|Client-Server-Architekturen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[High-Level-Kommunikation|hochabstrakte Kommunikation]], bei der [[Zugriffstransparenz]] oder [[Fehlertoleranz]] im Vordergrund stehen. Alternativen wie [[Remote Procedure Call|RPC]] oder [[Middleware]] (z. B. ZeroMQ) bieten mehr [[Abstraktion]] und [[Fehlerbehandlung]]. Sockets sind [[low-level]] und erfordern manuelle Verwaltung von [[Verbindung|Verbindungen]], [[Puffer|Puffern]] und [[Synchronisation|Synchronisation]].
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches [[Client-Server-Beispiel]] in Python, das das Berkeley Socket Interface nutzt:', 'server': {'code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.bind(('localhost', 12345))\ns.listen(1)\nconn, addr = s.accept()\ndata = conn.recv(1024)\nconn.send(data + b'*')\nconn.close()", 'erlaeuterung': 'Der Server erstellt einen [[Socket]], bindet ihn an eine [[Adresse]], wartet auf eine [[Verbindung]], empfängt [[Daten]] und sendet sie mit einem Sternchen zurück.'}, 'client': {'code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.connect(('localhost', 12345))\ns.send(b'Hello')\ndata = s.recv(1024)\nprint(data)\ns.close()", 'erlaeuterung': 'Der Client verbindet sich mit dem Server, sendet eine [[Nachricht]] und empfängt die Antwort.'}}
