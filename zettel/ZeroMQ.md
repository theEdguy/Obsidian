---
id: a5867894-335b-4c19-8158-4b087fcda698
title: "ZeroMQ"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte-kommunikation
  - verteilte-systeme
  - asynchrone-kommunikation
  - netzwerkprogrammierung
  - middleware
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[ZeroMQ]]

- **Kernkonzept:** ZeroMQ ist eine leichtgewichtige [[Nachrichtenbibliothek|Nachrichtenbibliotheken]], die asynchrone Kommunikation zwischen [[Prozess|Prozessen]] in [[Verteiltes System|verteilten Systemen]] durch vordefinierte [[Kommunikationsmuster]] wie Request-Reply, Publish-Subscribe und Pipeline vereinfacht.
- **Nutzen & Zweck:** ZeroMQ löst das [[Problem]] der komplexen [[Socket-Programmierung]] in [[Verteilte Systeme|verteilten Systemen]], indem es höhere Abstraktionen für [[Nachrichtenorientierte Kommunikation]] bereitstellt. Es reduziert [[Programmierfehler]] und beschleunigt die Entwicklung von [[Skalierbar|skalierbaren]] und [[Entkoppelt|entkoppelten]] [[Anwendung|Anwendungen]].
- **Abgrenzung & Grenzen:** ZeroMQ eignet sich nicht für [[Synchron|synchrone]] [[Kommunikation]] mit strikten [[Transaktionsgarantien]] oder [[Echtzeitanforderungen]]. Im Vergleich zu [[RPC]]-Frameworks wie [[gRPC]] fehlen [[Typensicherheit]] und [[IDL]]-Unterstützung. Für [[Persistente Nachrichten]] oder [[Message Broker]] wie [[Apache Kafka]] ist es weniger geeignet.
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches Request-Reply-Muster in ZeroMQ (Python):', 'server': {'code': 'import zmq\ncontext = zmq.Context()\ns = context.socket(zmq.REP)\ns.bind("tcp://*:5555")\nwhile True:\n    message = s.recv()\n    s.send(b"Reply: " + message)', 'erlaeuterung': 'Der Server wartet auf [[Nachricht|Nachrichten]] und antwortet mit einer modifizierten Version.'}, 'client': {'code': 'import zmq\ncontext = zmq.Context()\ns = context.socket(zmq.REQ)\ns.connect("tcp://localhost:5555")\ns.send(b"Hello")\nprint(s.recv())', 'erlaeuterung': 'Der Client sendet eine [[Nachricht]] und blockiert, bis die Antwort eintrifft.'}}
