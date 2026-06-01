---
id: c3bbee8f-134f-4c9a-b3fd-e0b1d91a16be
title: "Socket-Operationen (socket, bind, listen, accept, connect, send, receive, close)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - interprozesskommunikation
  - verteilte-systeme
  - low-level
  - socket-programmierung
  - tcp-ip
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Socket-Operationen (socket, bind, listen, accept, connect, send, receive, close)]]

- **Kernkonzept:** Socket-Operationen bilden die Grundlage für [[Nachrichtenorientierte Kommunikation|nachrichtenorientierte Kommunikationen]] in [[Verteilte Systeme|verteilten Systemen]], indem sie [[Endpunkt|Endpunkte]] für den Datenaustausch zwischen [[Prozess|Prozessen]] über [[Netzwerk|Netzwerke]] bereitstellen.
- **Nutzen & Zweck:** Dieses Konzept ermöglicht die [[Interprozesskommunikation]] zwischen [[Rechner|Rechnern]] oder [[Prozess|Prozessen]] auf einem [[System|System]], indem es eine standardisierte Schnittstelle für den Aufbau, die Verwaltung und den Abbau von [[Netzwerkverbindung|Netzwerkverbindungen]] bietet. Es löst das Problem der [[Datenübertragung]] in heterogenen Umgebungen und bildet die Basis für höhere [[Kommunikationsprotokoll|Kommunikationsprotokolle]] wie [[RPC]] oder [[HTTP]].
- **Abgrenzung & Grenzen:** Socket-Operationen sind [[Low-Level|low-level]] und erfordern manuelle Verwaltung von [[Verbindung|Verbindungen]], [[Fehler|Fehlern]] und [[Datenformat|Datenformaten]]. Sie sollten nicht genutzt werden, wenn höhere Abstraktionen wie [[RPC]], [[REST]] oder [[Message Queue|Message Queues]] (z. B. [[ZeroMQ]], [[RabbitMQ]]) verfügbar sind, die [[Zugriffstransparenz]] oder [[Fehlertoleranz]] besser unterstützen. Für [[Echtzeitkommunikation]] oder [[Streaming]] sind spezialisierte Protokolle wie [[WebSocket|WebSockets]] oft besser geeignet.
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches Beispiel für einen [[TCP-Socket|TCP-Socket]]-basierten [[Client-Server|Client-Server]]-Ablauf in Python:', 'server': {'code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.bind(('localhost', 12345))\ns.listen(1)\nconn, addr = s.accept()\ndata = conn.recv(1024)\nconn.send(data.upper().encode())\nconn.close()", 'erlaeuterung': 'Der Server erstellt einen Socket, bindet ihn an eine [[Adresse]] und [[Port]], wartet auf eine [[Verbindungsanfrage]], empfängt Daten, sendet eine modifizierte Antwort und schließt die Verbindung.'}, 'client': {'code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.connect(('localhost', 12345))\ns.send(b'Hello')\ndata = s.recv(1024)\nprint(data.decode())\ns.close()", 'erlaeuterung': 'Der Client verbindet sich mit dem Server, sendet eine Nachricht, empfängt die Antwort und schließt die Verbindung.'}}
