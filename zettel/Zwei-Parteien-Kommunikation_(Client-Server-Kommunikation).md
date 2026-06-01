---
id: 9dd68d2b-1b38-48b6-b79a-3ce7897f2baa
title: "Zwei-Parteien-Kommunikation (Client-Server-Kommunikation)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - kommunikation
  - client-server
  - verteilte-systeme
  - protokolle
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Zwei-Parteien-Kommunikation (Client-Server-Kommunikation)]]

- **Kernkonzept:** Die Zwei-Parteien-Kommunikation beschreibt ein [[Architekturstil|Architekturstils]], bei dem ein [[Client|Clients]] Anfragen an einen [[Server|Server]] sendet, der diese verarbeitet und eine Antwort zurückgibt. Dies ermöglicht die [[Trennung|Trennung]] von [[Aufgabe|Aufgaben]] in verteilten [[System|Systemen]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Koordination]] und [[Ressourcenverwaltung]] in verteilten [[System|Systemen]], indem es eine klare [[Rollenverteilung]] zwischen [[Anfrage|Anfragenden]] (Clients) und [[Dienstanbieter|Dienstanbietern]] (Servern) schafft. Es ermöglicht [[Skalierbarkeit]], [[Wiederverwendbarkeit]] von [[Dienst|Diensten]] und eine zentrale [[Steuerung]] von [[Ressource|Ressourcen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Szenario|Szenarien]], die hohe [[Echtzeitfähigkeit]] oder [[Entkopplung]] erfordern, wie z. B. [[Ereignisgesteuerte Systeme]] oder [[Publish-Subscribe-Architekturen]]. Im Vergleich zu [[Peer-to-Peer-Systemen]] fehlt die [[Symmetrie]] in der [[Kommunikation]], und bei hoher [[Last]] kann der Server zum [[Flaschenhals]] werden. Alternativen wie [[REST-Architekturen]] oder [[Microservices]] bieten oft flexiblere [[Interaktionsmuster]].
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches Beispiel für Client-Server-Kommunikation über Sockets in Python:', 'server_code': ['from socket import *', 's = socket(AF_INET, SOCK_STREAM)', "s.bind(('', 12345))", 's.listen(1)', '(conn, addr) = s.accept()', 'while True:', '    data = conn.recv(1024)', '    if not data: break', '    conn.send(data.upper())', 'conn.close()'], 'client_code': ['from socket import *', 's = socket(AF_INET, SOCK_STREAM)', "s.connect(('localhost', 12345))", "s.send(b'Hello, Server')", 'data = s.recv(1024)', 'print(data.decode())', 's.close()']}
