---
id: f41fcdca-64b9-478a-b0ed-232e7855ed28
title: "Synchrone und asynchrone RPCs"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - kommunikation
  - rpc
  - netzwerk
  - synchronisation
  - schnittstellen
  - architektur
  - parallelität
  - asynchron
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Synchrone und asynchrone RPCs]]

- **Kernkonzept:** [[Remote_Procedure_Call|RPCs]] ermöglichen die Ausführung von [[Prozedur|Prozeduren]] auf entfernten [[System|Systemen]], wobei zwischen synchronen und asynchronen [[Aufruf|Aufrufen]] unterschieden wird. Synchrone [[RPC|RPCs]] blockieren den [[Aufrufer]] bis zur [[Antwort]], während asynchrone [[RPC|RPCs]] eine [[nicht-blockierende]] [[Verarbeitung]] durch [[Parallelität]] ermöglichen.
- **Nutzen & Zweck:** [[Remote_Procedure_Call|RPCs]] lösen das [[Problem]] der [[Verteilungstransparenz]] in [[verteilten_Systemen|verteilten Systemen]], indem sie die [[Kommunikation]] zwischen [[Komponente|Komponenten]] vereinfachen und eine einheitliche [[Schnittstelle]] für entfernte [[Prozeduraufruf|Prozeduraufrufe]] bereitstellen. Synchrone [[RPC|RPCs]] eignen sich für [[Anwendung|Anwendungen]], die auf [[Ergebnis|Ergebnisse]] warten müssen, während asynchrone [[RPC|RPCs]] [[Latenz]] und [[Blockierung]] vermeiden und [[Effizienz]] durch [[Parallelität]] steigern. Sie sind besonders nützlich für [[langlaufende]] oder [[unabhängige]] [[Aufgabe|Aufgaben]] und ermöglichen [[ereignisgesteuerte]] [[Architektur|Architekturen]].
- **Abgrenzung & Grenzen:** Synchrone [[RPC|RPCs]] sind ungeeignet, wenn [[Latenz]] oder [[Blockierung]] des [[Aufrufers]] kritisch sind, da dieser auf die [[Antwort]] warten muss. Asynchrone [[RPC|RPCs]] sollten vermieden werden, wenn die [[Ergebnis|Ergebnisse]] des [[Aufruf|Aufrufs]] für die weitere [[Verarbeitung]] zwingend erforderlich sind oder wenn die [[Komplexität]] der [[Fehlerbehandlung]] (z. B. durch [[Callback|Callbacks]]) die [[Vorteile]] überwiegt. Beide [[RPC|RPC-Varianten]] sind ungeeignet für [[Multicast]]-Szenarien oder wenn [[Referenz|Referenzen]] auf entfernte Daten benötigt werden. Alternativen wie [[nachrichtenorientierte_Kommunikation]] (z. B. [[ZeroMQ]], [[Sockets]]) oder [[Event-basierte_Programmierung]] bieten mehr [[Flexibilität]] für [[nicht-blockierende]] oder [[ereignisgesteuerte]] [[Systeme]]. Asynchrone [[RPC|RPCs]] erfordern oft zusätzliche Mechanismen wie [[Event_Loop|Event-Loops]] oder [[Callback-Funktionen]], was die [[Implementierung]] komplexer gestaltet.
- **Beispiel / Code:** ### Synchrone RPCs (DCE RPC-ähnliche [[Schnittstellendefinition]] in [[IDL]]):
```idl
interface Beispiel {
    int incr([in, out] int *a, [in, out] int *b);
}
```

**Verhalten bei [[Copy-in/Copy-out-Semantik]]:**
- Lokale Ausführung (Referenzübergabe): `incr(i, i)` → `i = 2` (da zweimal inkrementiert).
- [[RPC]]-Ausführung: `incr(i, i)` → `i = 1` (da beide [[Parameter]] unabhängig kopiert und zurückgeschrieben werden).

---

### Asynchrone RPCs (Python mit ZeroMQ):
**Client-Code:**
```python
import zmq
context = zmq.Context()
socket = context.socket(zmq.REQ)
socket.connect("tcp://localhost:5555")
socket.send(b"Hole Daten")  # Kein Blockieren, Client kann weiterarbeiten
# Später:
antwort = socket.recv()  # Blockiert nur bei Abruf der Antwort
print(antwort)
```

**Server-Code (mit [[Callback-Mechanismus]]):**
```python
import zmq, threading

def verarbeite_anfrage(anfrage):
    # Simuliere langlaufende Verarbeitung
    threading.Event().wait(2)
    return anfrage + b" verarbeitet"

def callback(antwort, socket):
    socket.send(antwort)

context = zmq.Context()
socket = context.socket(zmq.REP)
socket.bind("tcp://*:5555")
while True:
    anfrage = socket.recv()
    thread = threading.Thread(target=lambda: callback(verarbeite_anfrage(anfrage), socket))
    thread.start()  # Antwort wird asynchron gesendet
```
