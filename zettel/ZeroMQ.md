---
id: 11d1c8cf-a362-5f53-b420-79feba794504
title: "ZeroMQ"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Kommunikation"
---

# [[ZeroMQ]]

- **Kernkonzept:** Bibliothek für asynchrones, nachrichtenorientiertes Transient Messaging. Kapselt systemnahe Sockets und bietet integrierte Muster wie Request-Reply (REQ/REP), Publish-Subscribe (PUB/SUB mit filterbasiertem Empfang) und Pipeline (PUSH/PULL für Lastverteilung).
- **Nutzen & Zweck:** Bibliothek für asynchrones, nachrichtenorientiertes Transient Messaging. Kapselt systemnahe Sockets und bietet integrierte Muster wie Request-Reply (REQ/REP), Publish-Subscribe (PUB/SUB mit filterbasiertem Empfang) und Pipeline (PUSH/PULL für Lastverteilung).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# Request-Reply Client (Python):
import zmq
ctx = zmq.Context()
s = ctx.socket(zmq.REQ)
s.connect('tcp://localhost:5555')
s.send(b'Hello')
msg = s.recv()
print(msg)
```
