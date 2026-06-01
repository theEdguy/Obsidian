---
id: 150863c2-38ff-4fcc-bf44-926bf35a256f
title: "Request/Response-Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - kommunikation
  - netzwerk
  - synchron
  - client-server
  - protokolle
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Request/Response-Kommunikation]]

- **Kernkonzept:** Die [[Request/Response-Kommunikation|Request/Response-Kommunikationsform]] ist ein synchrones [[Kommunikationsmuster|Muster]] in [[Verteilte Systeme|verteilten Systemen]], bei dem ein [[Client|Client]] eine [[Anfrage]] (Request) an einen [[Server]] sendet und auf dessen [[Antwort]] (Response) wartet.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der strukturierten [[Interaktion]] zwischen [[Komponenten]] in [[Verteilte Systeme|verteilten Systemen]], indem es eine klare [[Schnittstelle]] für den [[Datenaustausch]] und die [[Koordination]] bietet. Es ermöglicht [[Zuverlässigkeit]] und [[Vorhersagbarkeit]] bei der [[Kommunikation]], da der [[Client]] auf eine [[Antwort]] warten kann, bevor er weitere [[Aktionen]] ausführt.
- **Abgrenzung & Grenzen:** Die [[Request/Response-Kommunikation]] ist ungeeignet für [[Szenarien]], die [[Echtzeitfähigkeit]] oder [[Asynchronität]] erfordern, da der [[Client]] blockiert, bis die [[Antwort]] eintrifft. Alternativen wie [[Publish-Subscribe-Architekturen|Publish-Subscribe]] oder [[Event-Driven-Architekturen|ereignisgesteuerte Architekturen]] sind besser für [[lose Kopplung|lose gekoppelte]] oder [[temporale Entkopplung|temporal entkoppelte]] Systeme geeignet. Zudem skaliert sie schlechter bei hoher [[Last]], da jeder [[Request]] eine dedizierte [[Verbindung]] erfordert.
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches Beispiel für [[Request/Response-Kommunikation]] mit [[Sockets]] in Python, bei dem ein [[Client]] eine Nachricht an einen [[Server]] sendet und auf eine modifizierte [[Antwort]] wartet:', 'server_code': 'from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.bind((\'\', 12345))\ns.listen(1)\n(conn, addr) = s.accept()\nwhile True:\n    data = conn.recv(1024)\n    if not data: break\n    conn.send(str(data) + "*")\nconn.close()', 'client_code': "from socket import *\ns = socket(AF_INET, SOCK_STREAM)\ns.connect(('localhost', 12345))\ns.send('Hello, world')\ndata = s.recv(1024)\nprint(data)\ns.close()"}
