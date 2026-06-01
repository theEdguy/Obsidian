---
id: 1c6f2e8b-5160-4f70-86c8-acdcc0c5a7f4
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
  - client-server
  - synchronisation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Client-Server-Modell]]

- **Kernkonzept:** Das [[Client-Server-Modell]] ist ein [[Architekturstil]] in [[Verteilte_Systeme|verteilten Systemen]], bei dem [[Prozess|Prozesse]] in zwei [[Rolle|Rollen]] unterteilt werden: Der [[Client]] initiiert [[Request|Anfragen]], während der [[Server]] diese bearbeitet und [[Service|Dienste]] bereitstellt. Es basiert auf [[transiente Kommunikation|transienter]] und [[synchrone Kommunikation|synchroner]] [[Nachrichtenübertragung|Nachrichtenübertragung]] und ermöglicht die Trennung von [[Benutzerschnittstelle|Benutzerschnittstellen]] und [[Datenverarbeitung|Datenverarbeitungslogik]] sowie eine zentrale [[Ressourcenverwaltung]] und [[Koordination]] in [[Netzwerk|Netzwerken]].
- **Nutzen & Zweck:** Das Modell löst das [[Problem]] der skalierbaren und zentralen Bereitstellung von [[Ressource|Ressourcen]] und [[Dienst|Diensten]] in [[Verteilte_Systeme|verteilten Systemen]]. Es ermöglicht die [[Zentralisierung|Zentralisierung]] von [[Ressource|Ressourcen]] und [[Dienstleistung|Dienstleistungen]], um [[Skalierbarkeit]], [[Wartbarkeit]] und [[Sicherheit]] zu verbessern. Durch die klare Trennung der [[Verantwortlichkeit|Verantwortlichkeiten]] vereinfacht es die [[Lastverteilung]], sichere [[Zugriffskontrolle|Zugriffskontrollen]] und fördert die [[Verteilungstransparenz]]. Zudem erleichtert es die Integration von [[Middleware]]-Komponenten zur [[Kommunikation]] zwischen [[Client|Clients]] und [[Server|Servern]] und ermöglicht die effiziente [[Verteilung]] von [[Rechenleistung|Rechenleistungen]] und [[Daten]] in heterogenen Systemen.
- **Abgrenzung & Grenzen:** Das [[Client-Server-Modell]] ist ungeeignet für [[Peer-to-Peer-Systeme|dezentrale Architekturen]], bei denen alle [[Knoten|Knoten]] gleichberechtigt agieren, oder für [[Systeme]] mit symmetrischer [[Interaktion]]. Es kann zu [[Engpass|Engpässen]] führen, wenn der [[Server]] überlastet ist oder [[Netzwerk|Netzwerkprobleme]] auftreten. Zudem ist es anfällig für [[Ausfall|Ausfälle]], wenn der [[Server]] nicht erreichbar ist, und ungeeignet für [[Anwendung|Anwendungen]], die [[hohe Verfügbarkeit|hohe Verfügbarkeit]] ohne [[Blockierung|Blockierung]] des [[Client|Clients]] erfordern, wie z. B. [[Echtzeitkommunikation]]. Alternativen wie [[Peer-to-Peer-Systeme]], [[Publish-Subscribe-Architekturen]] (z. B. [[Linda-Tupelraum]]), [[Message-oriented Middleware (MOM)|MOM]], [[Microservices]] oder [[Event-driven-Architecture|ereignisgesteuerte Architekturen]] bieten mehr Flexibilität in dynamischen Umgebungen. Bei [[Legacy-Systeme|Legacy-Systemen]] können [[Wrapper]] oder [[Interzeptoren]] nötig sein, um [[Kompatibilität]] herzustellen.
- **Beispiel / Code:** Das [[Client-Server-Modell]] lässt sich durch verschiedene [[Protokoll|Protokolle]] und [[Technologie|Technologien]] implementieren. Hier zwei Beispiele in Python:

**1. Socket-basierte Kommunikation (transient & synchron):**
```python
# Server (Dienstbereitstellung)
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 12345))
server_socket.listen(1)

while True:
    conn, addr = server_socket.accept()
    data = conn.recv(1024)
    if data == b'Hello':
        conn.send(b'Hello, Client!')
    elif data == b'GET_TIME':
        reply = 'Aktuelle Zeit: 14:30'
        conn.send(reply.encode())
    conn.close()

# Client (Dienstanfrage)
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(('localhost', 12345))
client_socket.send(b'Hello')
response = client_socket.recv(1024)
print(response.decode())
client_socket.close()
```

**2. HTTP-basierte Kommunikation (standardisiertes Protokoll):**
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

*Erläuterung:* Beide Beispiele zeigen die [[Request]]-Reply-Kommunikation, wobei der [[Server]] auf [[Anfrage|Anfragen]] des [[Client|Clients]] reagiert. Der [[Client]] muss während der [[Kommunikation]] aktiv bleiben (synchrone [[Interaktion]]). Der HTTP-Server demonstriert zudem die Nutzung standardisierter [[Protokoll|Protokolle]] wie HTTP für [[Kommunikation]] in [[Verteilte_Systeme|verteilten Systemen]].
