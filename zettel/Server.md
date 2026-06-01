---
id: f991c607-fa2e-492d-ba26-344d82fbdca9
title: "Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - architektur
  - nebenläufigkeit
  - cloud_computing
  - virtualisierung
  - kommunikation
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Server]]

- **Kernkonzept:** Ein [[Server]] ist ein [[Prozess|Prozesse]], der einen [[Dienst|Dienste]] für [[Client|Clients]] bereitstellt, indem er auf eingehende [[Anfrage|Anfragen]] wartet und diese bearbeitet. Er ermöglicht die zentrale Bereitstellung von [[Ressource|Ressourcen]] und [[Funktionalität|Funktionalitäten]] in verteilten [[System|Systemen]].
- **Nutzen & Zweck:** Ein [[Server]] löst das Problem der zentralen Verwaltung und Bereitstellung von [[Ressource|Ressourcen]] und [[Dienst|Diensten]] in verteilten [[System|Systemen]]. Er ermöglicht [[Skalierbarkeit]], [[Lastverteilung]] und [[Isolation]] zwischen [[Client|Clients]], z. B. durch [[Virtualisierung]] oder [[Cloud-Computing]]-Modelle wie [[IaaS]], [[PaaS]] und [[SaaS]]. Zudem vereinfacht er die [[Koordination]] und [[Kommunikation]] zwischen mehreren [[Prozess|Prozessen]].
- **Abgrenzung & Grenzen:** Ein [[Server]] sollte nicht genutzt werden, wenn [[Echtzeitanforderung|Echtzeitanforderungen]] oder extrem niedrige [[Latenz]] kritisch sind, da Netzwerkkommunikation und [[Nebenläufigkeit]] zusätzliche [[Overhead|Overheads]] verursachen. Alternativen wie [[Peer-to-Peer]]-Systeme oder [[Edge-Computing]] können in solchen Fällen besser geeignet sein. Zudem sind [[zustandslose Server]] weniger performant, wenn [[Client]]-Verhalten antizipiert werden muss (z. B. [[Caching]] oder [[Vorauslesen]]).
- **Beispiel / Code:** Ein einfaches Beispiel für einen [[iterativen Server]] in Python mit TCP-Sockets:

```python
import socket

HOST = '127.0.0.1'
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    conn, addr = s.accept()
    with conn:
        print(f"Verbunden mit {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)  # Echo-Server
```

Ein [[nebenläufiger Server]] würde stattdessen für jede [[Anfrage]] einen neuen [[Thread]] oder [[Prozess]] starten.
