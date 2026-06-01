---
id: 85791b70-10e4-4a73-850c-c15da872dcc2
title: "Client-Server-Modell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - netzwerk
  - middleware
  - request-reply
  - zentralisierung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Client-Server-Modell]]

- **Kernkonzept:** Das [[Client-Server-Modell]] ist ein Architekturstil in [[Verteilte Systeme|verteilten Systemen]], bei dem [[Prozess|Prozesse]] in [[Server]] (Dienstanbieter) und [[Client|Clients]] (Dienstnutzer) unterteilt werden. [[Server]] erbringen [[Service|Services]], während [[Client|Clients]] diese über [[Request]]-Reply-Kommunikation anfordern.
- **Nutzen & Zweck:** Das Modell löst das Problem der zentralen [[Ressourcenverwaltung]] und [[Koordination]] in [[Netzwerk|Netzwerken]], indem es eine klare Trennung zwischen Diensterbringung und -nutzung ermöglicht. Es vereinfacht die [[Skalierbarkeit]], [[Wartbarkeit]] und [[Sicherheit]] durch zentrale Kontrolle der [[Ressource|Ressourcen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit hoher [[Dezentralisierung]] oder symmetrischer [[Interaktion]], da es eine hierarchische Struktur voraussetzt. Alternativen wie [[Peer-to-Peer-Systeme]] oder [[Publish-Subscribe-Architekturen]] (z. B. [[Linda-Tupelraum]]) sind besser für gleichberechtigte [[Prozess|Prozesse]] oder ereignisgesteuerte Kommunikation. Bei [[Legacy-Systeme|Legacy-Systemen]] können [[Wrapper]] oder [[Interzeptoren]] nötig sein, um Kompatibilität herzustellen.
- **Beispiel / Code:** Ein einfaches Beispiel für eine Client-Server-Interaktion in Python (Pseudocode):

**Server (Dienstbereitstellung):**
```python
from socket import *
server_socket = socket(AF_INET, SOCK_STREAM)
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
while True:
    connection, addr = server_socket.accept()
    data = connection.recv(1024).decode()
    if data == 'GET_TIME':
        reply = 'Aktuelle Zeit: 14:30'
    connection.send(reply.encode())
    connection.close()
```

**Client (Dienstanfrage):**
```python
from socket import *
client_socket = socket(AF_INET, SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.send('GET_TIME'.encode())
response = client_socket.recv(1024).decode()
print(response)
client_socket.close()
```
