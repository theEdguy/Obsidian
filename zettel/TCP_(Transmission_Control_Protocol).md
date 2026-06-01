---
id: 387869e8-d4d0-4647-aa5f-5a7040109478
title: "TCP (Transmission Control Protocol)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - transportschicht
  - protokoll
  - verteilte-systeme
  - kommunikation
  - zuverlässigkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[TCP (Transmission Control Protocol)]]

- **Kernkonzept:** TCP ist ein [[Protokoll|Protokolle]] der [[Transportschicht]] im [[Netzwerk|Netzwerkmodell]], das [[verbindungsorientierte]], [[verlässliche]] [[Datenübertragung|Datenübertragungen]] zwischen [[Prozess|Prozessen]] in [[verteilten Systemen]] ermöglicht.
- **Nutzen & Zweck:** TCP löst das [[Problem]] der [[unzuverlässigen]] [[Datenübertragung]] in [[Netzwerken]], indem es [[Fehlererkennung]], [[Flusskontrolle]] und [[Neuübertragung]] verlorener [[Paket|Pakete]] garantiert. Es stellt sicher, dass [[Datenstrom|Datenströme]] in der richtigen Reihenfolge und ohne Verluste beim Empfänger ankommen, was für [[Anwendung|Anwendungen]] wie [[Web]] oder [[E-Mail]] essenziell ist.
- **Abgrenzung & Grenzen:** TCP sollte nicht genutzt werden, wenn [[Latenz]] kritischer ist als [[Zuverlässigkeit]] (z. B. bei [[Echtzeitkommunikation]] wie [[VoIP]] oder [[Video-Streaming]]). Alternativen wie [[UDP]] bieten hier [[geringere]] [[Verzögerung|Verzögerungen]], da sie auf [[Fehlerkorrektur]] und [[Reihenfolgegarantien]] verzichten. Zudem ist TCP für [[transiente Kommunikation]] ungeeignet, da es eine [[Verbindung]] voraussetzt.
- **Beispiel / Code:** Ein einfaches Beispiel in Python zur Nutzung von TCP mit dem `socket`-Modul:

```python
import socket

# Server
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
conn, addr = server_socket.accept()
data = conn.recv(1024)
print(f"Empfangen: {data.decode()}")
conn.sendall(b"Nachricht erhalten")
conn.close()

# Client
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.sendall(b"Hallo Server!")
response = client_socket.recv(1024)
print(f"Antwort: {response.decode()}")
client_socket.close()
```
