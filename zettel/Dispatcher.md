---
id: 40ab8033-380e-4571-9724-bb49085aaccb
title: "Dispatcher"
date: 2026-06-01
tags:
  - verteilte_systeme
  - server_architektur
  - nebenläufigkeit
  - netzwerk
  - koordination
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Dispatcher]]

- **Kernkonzept:** Ein [[Dispatcher]] ist ein zentraler [[Koordinationsmechanismus|Koordinationsmechanismus]] in [[nebenläufigen_Servern|nebenläufigen Servern]], der eingehende [[Anfragen|Anfrage]] annimmt und an separate [[Threads|Thread]] oder [[Prozesse]] zur Bearbeitung weiterleitet.
- **Nutzen & Zweck:** Der [[Dispatcher]] löst das [[Problem]] der effizienten [[Anfrageverarbeitung]] in [[verteilten_Systemen|verteilten Systemen]], indem er [[Skalierbarkeit]] und [[Nebenläufigkeit]] ermöglicht. Ohne ihn müssten [[Server]] [[Anfragen]] sequenziell abarbeiten, was zu [[Engpässen]] und schlechter [[Auslastung]] führt.
- **Abgrenzung & Grenzen:** Ein [[Dispatcher]] ist nicht sinnvoll für [[iterative_Server|iterative Server]], die [[Anfragen]] nacheinander abarbeiten. Bei einfachen [[Diensten]] mit geringer [[Last]] kann der Overhead der [[Thread]]- oder [[Prozessverwaltung]] die Vorteile überwiegen. Alternativen wie [[Event-Loops]] oder [[asynchrone_Programmierung|asynchrone Programmierung]] können in bestimmten Szenarien effizienter sein.
- **Beispiel / Code:** Ein einfaches Beispiel in Python mit dem `socketserver`-Modul:

```python
import socketserver

class RequestHandler(socketserver.BaseRequestHandler):
    def handle(self):
        data = self.request.recv(1024)
        print(f"Anfrage von {self.client_address}: {data.decode()}")
        self.request.sendall(b"Anfrage bearbeitet")

if __name__ == "__main__":
    with socketserver.ThreadingTCPServer(("localhost", 8080), RequestHandler) as server:
        print("Dispatcher läuft auf Port 8080...")
        server.serve_forever()
```

Hier übernimmt der `ThreadingTCPServer` die Rolle des [[Dispatchers]], indem er jede [[Anfrage]] an einen neuen [[Thread]] weiterleitet.
