---
id: 2a8da85a-011e-4640-a9e4-b5fae9bbe830
title: "Multicast RPC"
date: 2026-06-01
tags:
  - verteilte_systeme
  - rpc
  - netzwerkkommunikation
  - skalierbarkeit
  - koordination
  - multicast
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Multicast RPC]]

- **Kernkonzept:** Multicast [[Remote Procedure Call|RPCs]] ermöglichen das gleichzeitige Senden eines [[Prozeduraufruf|Prozeduraufrufs]] an eine Gruppe von [[Server|Servern]], um verteilte [[Berechnung|Berechnungen]] oder [[Koordination|Koordinationen]] effizient durchzuführen.
- **Nutzen & Zweck:** Das Konzept löst das Problem der synchronen [[Kommunikation]] mit mehreren [[Empfänger|Empfängern]] in [[Verteilte Systeme|verteilten Systemen]], indem es [[Skalierbarkeit]] und [[Konsistenz]] bei Gruppenoperationen verbessert. Es reduziert den [[Overhead]] im Vergleich zu einzelnen [[RPC|RPCs]] und ermöglicht [[Echtzeit]]-Synchronisation.
- **Abgrenzung & Grenzen:** Multicast [[RPC]] ist ungeeignet für [[Anwendung|Anwendungen]], die [[Unicast]]- oder [[Broadcast]]-Kommunikation erfordern, da es zusätzliche [[Komplexität]] in der [[Fehlerbehandlung]] und [[Gruppenverwaltung]] mit sich bringt. Im Gegensatz zu [[asynchroner RPC|asynchronen RPCs]] blockiert es nicht, erfordert aber [[Zuverlässigkeit]] in der [[Netzwerk]]-Infrastruktur. Für [[Einzeloperationen]] ist ein einfacher [[RPC]] oft ausreichend.
- **Beispiel / Code:** Ein Beispiel für Multicast RPC in ZeroMQ (vereinfacht):

**Client (Sender):**
```python
import zmq
context = zmq.Context()
socket = context.socket(zmq.PUB)
socket.bind("tcp://*:5555")
socket.send(b"UPDATE_DATA 42")  # Nachricht an alle Subscriber
```

**Server (Empfänger, mehrere Instanzen):**
```python
import zmq
context = zmq.Context()
socket = context.socket(zmq.SUB)
socket.connect("tcp://server1:5555")
socket.setsockopt(zmq.SUBSCRIBE, b"UPDATE_DATA")
message = socket.recv()  # Erhält die Nachricht von allen Sendern
```
