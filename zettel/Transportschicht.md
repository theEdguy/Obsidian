---
id: a697023f-ec5c-4890-b9a3-0778645ee68d
title: "Transportschicht"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - protokolle
  - verteilte-systeme
  - osi-modell
  - transportprotokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Transportschicht]]

- **Kernkonzept:** Die Transportschicht ist die vierte Schicht im [[OSI-Referenzmodell|OSI-Referenzmodell]] und stellt [[Kommunikationsmechanismus|Kommunikationsmechanismen]] für [[verteilte Systeme]] bereit, indem sie [[Ende-zu-Ende-Kommunikation]] zwischen [[Prozess|Prozessen]] ermöglicht.
- **Nutzen & Zweck:** Sie löst das Problem der zuverlässigen oder effizienten Datenübertragung zwischen [[Anwendung|Anwendungen]] über [[Netzwerk|Netzwerke]] hinweg, indem sie Dienste wie [[Flusskontrolle]], [[Fehlererkennung]] und [[Verbindungsmanagement]] bereitstellt. Dadurch wird die Komplexität der [[Hardware]]-nahen Schichten abstrahiert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]], die direkte [[Hardware]]-nahe Steuerung benötigen (z. B. Echtzeit-Systeme mit extrem niedriger Latenz). Alternativen wie [[Middleware]] oder [[Message-oriented Middleware]] bieten höhere Abstraktionsebenen für persistente oder asynchrone [[Kommunikation]]. Die Transportschicht selbst bietet keine [[Sicherheitsmechanismus|Sicherheitsmechanismen]] wie Verschlüsselung (diese werden in höheren Schichten realisiert).
- **Beispiel / Code:** Ein einfaches Beispiel für die Nutzung von TCP (verbindungsorientiert) in Python:

```python
import socket

# Server
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
conn, addr = server_socket.accept()
data = conn.recv(1024)
print(f"Empfangen: {data.decode()}")
conn.sendall(b"Antwort vom Server")
conn.close()

# Client
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.sendall(b"Anfrage vom Client")
response = client_socket.recv(1024)
print(f"Server antwortet: {response.decode()}")
client_socket.close()
```

Für UDP (unzuverlässig, verbindungslos) wird `socket.SOCK_DGRAM` verwendet.
