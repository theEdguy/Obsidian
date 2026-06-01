---
id: d36e2668-fece-4e27-8b39-7e9efe3a76ec
title: "Request/Reply-Modell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - kommunikation
  - client-server
  - synchron
  - netzwerk
  - middleware
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Request/Reply-Modell]]

- **Kernkonzept:** Das Request/Reply-Modell beschreibt ein [[Kommunikationsmuster|Kommunikationsmuster]] in [[Verteilte Systeme|verteilten Systemen]], bei dem ein [[Client]] eine Anfrage (Request) an einen [[Server]] sendet und auf eine Antwort (Reply) wartet.
- **Nutzen & Zweck:** Es löst das Problem der synchronen [[Koordination]] zwischen [[Prozess|Prozessen]] in [[Client-Server-Architekturen]], indem es eine einfache und zuverlässige [[Interaktion]] ermöglicht. Besonders nützlich für [[Dienst|Dienste]], die eine direkte Bestätigung oder Ergebnisrückgabe erfordern.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[asynchrone Kommunikation]], bei der keine sofortige Antwort benötigt wird (z. B. [[Publish-Subscribe-Modell]] oder [[Tupelraum]]-basierte Systeme wie [[Linda]]). Auch ineffizient bei hohen [[Latenz|Latenzen]] oder unzuverlässigen [[Netzwerk|Netzwerken]], da der [[Client]] blockiert. Alternativen wie [[Message-Passing]] oder [[Event-basierte Systeme]] bieten mehr Flexibilität.
- **Beispiel / Code:** Ein einfaches Beispiel in Python mit Socket-Programmierung:

**Client (Request-Sender):**
```python
import socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(('localhost', 12345))
client.send(b'Hallo Server!')
reply = client.recv(1024)
print('Antwort:', reply.decode())
client.close()
```

**Server (Reply-Sender):**
```python
import socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind(('localhost', 12345))
server.listen(1)
conn, addr = server.accept()
request = conn.recv(1024)
print('Anfrage:', request.decode())
conn.send(b'Hallo Client!')
conn.close()
```
