---
id: 887eca2c-98ac-4537-9453-3178ef1212b5
title: "Request-Reply Muster"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikationsmuster
  - verteilte-systeme
  - synchronisation
  - client-server
  - netzwerk
  - rpc
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Request-Reply Muster]]

- **Kernkonzept:** Das Request-Reply Muster ist ein [[Kommunikationsmuster|Kommunikationsmuster]] in [[Verteilte Systeme|verteilten Systemen]], bei dem ein [[Client]] eine Anfrage (Request) an einen [[Server]] sendet und auf eine Antwort (Reply) wartet, bevor er fortfährt.
- **Nutzen & Zweck:** Es löst das Problem der synchronen [[Koordination]] zwischen [[Prozess|Prozessen]] in [[Verteilte Systeme|verteilten Systemen]], indem es eine einfache und intuitive [[Schnittstelle]] für entfernte [[Prozeduraufruf|Prozeduraufrufe]] (RPC) bietet. Es ermöglicht die [[Abstraktion]] von Netzwerkdetails und vereinfacht die [[Implementierung]] von [[Client-Server-Architekturen]].
- **Abgrenzung & Grenzen:** Das Muster ist ungeeignet für Szenarien, die asynchrone [[Kommunikation]] oder [[Ereignisgesteuerte Architektur|ereignisgesteuerte Architekturen]] erfordern, da es zu [[Blockierung|Blockierungen]] führen kann. Alternativen wie [[Publish-Subscribe]] oder [[Pipeline-Muster]] sind besser für lose [[Kopplung]] oder [[Datenstromverarbeitung]] geeignet. Zudem skaliert es schlecht bei hoher [[Latenz]] oder vielen gleichzeitigen Anfragen.
- **Beispiel / Code:** Ein einfaches Beispiel in ZeroMQ (Python):

**Server (REP-Socket):**
```python
import zmq
context = zmq.Context()
s = context.socket(zmq.REP)
s.bind("tcp://*:5555")
while True:
    message = s.recv()
    s.send(message + "*")
```

**Client (REQ-Socket):**
```python
import zmq
context = zmq.Context()
s = context.socket(zmq.REQ)
s.connect("tcp://localhost:5555")
s.send("Hello")
reply = s.recv()
print(reply)  # Ausgabe: "Hello*"
```
