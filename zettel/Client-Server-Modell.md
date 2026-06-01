---
id: e5c5cb98-805b-42aa-935b-7134456bd39f
title: "Client-Server-Modell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - middleware
  - request-reply
  - zentralisierung
  - kommunikation
  - koordination
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Client-Server-Modell]]

- **Kernkonzept:** Das [[Client-Server-Modell]] ist ein [[Architekturstil]] in [[Verteilte_Systeme|verteilten Systemen]], bei dem [[Prozess|Prozesse]] in zwei [[Rolle|Rollen]] unterteilt werden: Der [[Client]] initiiert [[Request|Anfragen]], während der [[Server]] diese bearbeitet und [[Service|Dienste]] bereitstellt. Es ermöglicht die Trennung von [[Benutzerschnittstelle|Benutzerschnittstellen]] und [[Datenverarbeitung|Datenverarbeitungslogik]] sowie eine zentrale [[Ressourcenverwaltung]] und [[Koordination]] in [[Netzwerk|Netzwerken]].
- **Nutzen & Zweck:** Das Modell löst das [[Problem]] der skalierbaren und zentralen Bereitstellung von [[Ressource|Ressourcen]] und [[Dienst|Diensten]] in [[Verteilte_Systeme|verteilten Systemen]]. Es vereinfacht die [[Skalierbarkeit]], [[Wartbarkeit]] und [[Sicherheit]] durch klare Trennung der Verantwortlichkeiten und ermöglicht [[Lastverteilung|Lastverteilungen]] sowie sichere [[Zugriffskontrolle|Zugriffskontrollen]]. Zudem fördert es die [[Verteilungstransparenz]] und erleichtert die Integration von [[Middleware]]-Komponenten zur [[Kommunikation]] zwischen [[Client|Clients]] und [[Server|Servern]].
- **Abgrenzung & Grenzen:** Das [[Client-Server-Modell]] ist ungeeignet für [[Peer-to-Peer-Systeme|dezentrale Architekturen]], bei denen alle [[Knoten|Knoten]] gleichberechtigt agieren, oder für [[Systeme]] mit symmetrischer [[Interaktion]]. Es kann zu [[Engpass|Engpässen]] führen, wenn der [[Server]] überlastet ist oder [[Netzwerk|Netzwerkprobleme]] auftreten. Alternativen wie [[Peer-to-Peer-Systeme]], [[Publish-Subscribe-Architekturen]] (z. B. [[Linda-Tupelraum]]), [[Microservices]] oder [[Event-driven-Architektur|ereignisgesteuerte Architekturen]] bieten mehr Flexibilität in dynamischen Umgebungen. Bei [[Legacy-Systeme|Legacy-Systemen]] können [[Wrapper]] oder [[Interzeptoren]] nötig sein, um [[Kompatibilität]] herzustellen.
- **Beispiel / Code:** Einfache Beispiele für [[Client-Server-Modell|Client-Server-Interaktionen]] in Python:

**1. Socket-basierte Kommunikation (Pseudocode):**
```python
# Server (Dienstbereitstellung)
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

# Client (Dienstanfrage)
from socket import *
client_socket = socket(AF_INET, SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.send('GET_TIME'.encode())
response = client_socket.recv(1024).decode()
print(response)
client_socket.close()
```

**2. HTTP-basierte Kommunikation:**
```python
# Server (server.py)
from http.server import BaseHTTPRequestHandler, HTTPServer

class SimpleHTTPRequestHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type', 'text/html')
        self.end_headers()
        self.wfile.write(b"<h1>Hallo vom Server!</h1>")

HTTPServer(('localhost', 8000), SimpleHTTPRequestHandler).serve_forever()

# Client (client.py)
import requests
response = requests.get('http://localhost:8000')
print(response.text)  # Ausgabe: <h1>Hallo vom Server!</h1>
```

Beide Beispiele zeigen die [[Request]]-Reply-Kommunikation, wobei der [[Server]] auf [[Anfrage|Anfragen]] des [[Client|Clients]] reagiert. Der HTTP-Server demonstriert zudem die Nutzung von [[Protokoll|Protokollen]] wie HTTP für standardisierte [[Kommunikation]].
