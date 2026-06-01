---
id: 587171e8-0503-49d5-a7b8-fda7a041e124
title: "Sockets (Netzwerkprogrammierung)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerkprogrammierung
  - verteilte-systeme
  - interprozesskommunikation
  - client-server
  - socket-api
  - tcp-ip
  - architektur
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Sockets (Netzwerkprogrammierung)]]

- **Kernkonzept:** Sockets sind [[Endpunkt|Endpunkte]] für die [[Kommunikation|Kommunikationen]] zwischen [[Prozess|Prozessen]] über ein [[Netzwerk]], die den Austausch von [[Daten|Daten]] nach dem [[Client-Server-Modell]] ermöglichen. Sie bilden die Grundlage für [[geschichtete Architekturen]] in [[verteilten Systemen]] und abstrahieren [[Netzwerkprotokoll|Netzwerkprotokolle]] wie TCP/IP.
- **Nutzen & Zweck:** Sockets lösen das [[Problem]] der [[Interprozesskommunikation]] über [[Rechnergrenze|Rechnergrenzen]] hinweg, indem sie eine standardisierte [[Schnittstelle]] für den [[Datenfluss]] zwischen [[Anwendung|Anwendungen]] bereitstellen. Sie ermöglichen [[Echtzeitkommunikation]], [[Datenübertragung]] und die [[Implementierung]] [[verteilter Anwendungen]] wie [[Webserver]], [[Chat-Systeme]] oder [[Datenbankverbindungen]].
- **Abgrenzung & Grenzen:** Sockets sind [[Low-Level-Konzept|Low-Level-Konzepte]] und erfordern manuelle [[Fehlerbehandlung]] (z. B. [[Verbindungsabbrüche]]). Für [[High-Level-Kommunikation]] sollten [[Abstraktion|Abstraktionen]] wie [[RPC (Remote Procedure Call)]], [[REST-APIs]] oder [[Message-Queues]] bevorzugt werden, die [[Skalierbarkeit]] und [[Wartbarkeit]] verbessern. Sockets sind ungeeignet für [[Publish-Subscribe-Systeme]] oder [[transaktionale Kommunikation]], da sie keine [[Entkopplung]] oder [[Persistenz]] bieten.
- **Beispiel / Code:** {'beschreibung': 'Beispiel für eine einfache [[Client-Server-Kommunikation]] mit TCP-Sockets in Python:', 'server_code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.bind(('localhost', 12345))\ns.listen(1)\n(conn, addr) = s.accept()\ndata = conn.recv(1024)\nconn.send(data.upper().encode())\nconn.close()", 'client_code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.connect(('localhost', 12345))\ns.send(b'Hello')\ndata = s.recv(1024)\nprint(data.decode())\ns.close()", 'hinweis': 'Der [[Server]] wartet auf [[Verbindungsanfrage|Verbindungsanfragen]], der [[Client]] initiiert die [[Kommunikation]]. Die [[Daten]] werden als [[Byte-String|Byte-Strings]] gesendet/empfangen.'}
