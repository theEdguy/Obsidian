---
id: bf3eed85-4f90-4171-b33c-c57475c08ce7
title: "Callback-Mechanismus"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - asynchron
  - kommunikation
  - rpc
  - ereignisgesteuert
  - netzwerk
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Callback-Mechanismus]]

- **Kernkonzept:** Ein [[Callback-Mechanismus|Callback-Mechanismus]] ermöglicht es einem [[System|Systemen]], asynchron auf [[Ereignis|Ereignisse]] oder [[Ergebnis|Ergebnisse]] zu reagieren, indem eine [[Funktion|Funktion]] (der Callback) bei Eintritt eines bestimmten [[Zustand|Zustands]] automatisch ausgeführt wird. Dies wird häufig in [[Verteilte Systeme|verteilten Systemen]] genutzt, um [[Blockierung|Blockierungen]] zu vermeiden.
- **Nutzen & Zweck:** Der [[Callback-Mechanismus|Callback-Mechanismus]] löst das [[Problem]] der [[Synchronisation|synchronen]] [[Wartezeit|Wartezeiten]] in [[Verteilte Systeme|verteilten Systemen]], indem er [[Client|Clients]] erlaubt, nach dem [[Aufruf]] einer [[Prozedur]] weiterzuarbeiten, ohne auf die [[Antwort]] des [[Server|Servers]] warten zu müssen. Dies verbessert die [[Effizienz]] und [[Skalierbarkeit]] von [[System|Systemen]].
- **Abgrenzung & Grenzen:** Ein [[Callback-Mechanismus]] sollte nicht genutzt werden, wenn eine [[Sequenz|sequenzielle]] oder [[Transaktion|transaktionale]] [[Verarbeitung]] erforderlich ist, da die [[Asynchronität]] die [[Kontrolle]] über den [[Ablauf]] erschwert. Alternativen wie [[Synchroner RPC|synchrone RPCs]] oder [[Nachrichtenwarteschlange|Nachrichtenwarteschlangen]] sind besser geeignet, wenn [[Determinismus]] oder [[Fehlerbehandlung]] priorisiert werden müssen.
- **Beispiel / Code:** Ein Beispiel für einen asynchronen [[RPC]] mit [[Callback-Mechanismus]] in [[ZeroMQ]] (vereinfacht):

**Client-Code (Python mit ZeroMQ REQ/REP-Muster):**
```python
import zmq
context = zmq.Context()
socket = context.socket(zmq.REQ)
socket.connect("tcp://localhost:5555")
# Asynchroner Aufruf mit Callback-Funktion
def callback(response):
    print(f"Ergebnis: {response}")
socket.send(b"Berechne etwas")
# Client arbeitet weiter, ohne zu blockieren
# ... später:
response = socket.recv()
callback(response)
```

**Server-Code (ZeroMQ REP-Socket):**
```python
import zmq
context = zmq.Context()
socket = context.socket(zmq.REP)
socket.bind("tcp://*:5555")
while True:
    request = socket.recv()
    # Verarbeitung...
    socket.send(b"Ergebnis der Berechnung")
```
