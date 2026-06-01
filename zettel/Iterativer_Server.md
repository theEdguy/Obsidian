---
id: dff22c04-dd40-4fd8-82da-71921040fcef
title: "Iterativer Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - server
  - netzwerk
  - architektur
  - verteilte-systeme
  - nebenläufigkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Iterativer Server]]

- **Kernkonzept:** Ein [[iterativer Server|iterativer Server]] bearbeitet [[Anfrage|Anfragen]] von [[Client|Clients]] nacheinander, indem er jeweils eine [[Anfrage]] vollständig abarbeitet, bevor er zur nächsten übergeht. Dies vereinfacht die [[Koordination]] und [[Synchronisation]] der [[Ressource|Ressourcen]].
- **Nutzen & Zweck:** Dieses Konzept existiert, um einfache [[Dienst|Dienste]] mit geringem [[Koordinationsaufwand]] umzusetzen. Es löst das [[Problem]] der [[Nebenläufigkeit]], indem es [[Anfrage|Anfragen]] sequenziell verarbeitet und so [[Race Condition|Race Conditions]] oder [[Deadlock|Deadlocks]] vermeidet. Besonders geeignet für [[Dienst|Dienste]] mit kurzen [[Bearbeitungszeit|Bearbeitungszeiten]] oder geringer [[Last]].
- **Abgrenzung & Grenzen:** Ein [[iterativer Server]] sollte nicht genutzt werden, wenn [[Anfrage|Anfragen]] blockierende [[Operation|Operationen]] (z. B. [[Dateizugriff|Dateizugriffe]] oder [[Netzwerkkommunikation]]) enthalten oder wenn hohe [[Skalierbarkeit]] erforderlich ist. Im Vergleich zu [[nebenläufigen Server|nebenläufigen Servern]] kann er [[Anfrage|Anfragen]] nicht parallel bearbeiten, was zu [[Latenz|Latenzen]] führt. [[Nebenläufige Server]] sind hier die bessere [[Alternative]].
- **Beispiel / Code:** Ein einfacher iterativer TCP-Server in Python:
```python
import socket

HOST = '127.0.0.1'
PORT = 65432

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    while True:
        conn, addr = s.accept()
        with conn:
            print(f'Verbunden mit {addr}')
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)  # Echo-Server
```
Der Server bearbeitet jeweils eine [[Verbindung]] und schließt sie ab, bevor er die nächste akzeptiert.
