---
id: 8fcf7dab-8f71-4520-a6bf-bd30e10d03bf
title: "Architekturstil"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - entwurfsmuster
  - software-engineering
  - kommunikation
  - modularitaet
  - software-design
  - komponenten
  - schnittstellen
  - konnektoren
  - schichtenmodell
  - rest
  - publish-subscribe
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Architekturstil]]

- **Kernkonzept:** Ein [[Architekturstil]] definiert generelle [[Prinzip|Prinzipien]] und [[Entwurfsmuster|Muster]] für den Entwurf von [[Architektur|Architekturen]] in [[Verteiltes_System|verteilten Systemen]], insbesondere durch die Strukturierung von [[Komponente|Komponenten]], deren [[Schnittstelle|Schnittstellen]] und [[Konnektor|Konnektoren]]. Er dient als wiederverwendbare Vorlage zur Lösung wiederkehrender [[Entwurfsproblem|Entwurfsprobleme]] und standardisiert die [[Interaktion]] zwischen [[Komponente|Komponenten]] sowie den [[Datenfluss]] im System.
- **Nutzen & Zweck:** Ein [[Architekturstil]] bietet einen wiederverwendbaren Rahmen, um die [[Komplexität]] in [[Verteiltes_System|verteilten Systemen]] zu reduzieren, die [[Wartbarkeit]] zu verbessern und die [[Kommunikation]] zwischen [[Komponente|Komponenten]] zu standardisieren. Durch die Vorgabe bewährter [[Muster]] für [[Interaktion]] und [[Datenfluss]] löst er das [[Problem]] unstrukturierter Systemgestaltung und fördert [[Skalierbarkeit]], [[Modularität]] sowie [[Fehlertoleranz]]. Zudem erleichtert er die [[Dokumentation]] und [[Kommunikation]] im [[Entwicklerteam|Team]], indem er eine gemeinsame [[Sprache]] und Struktur vorgibt.
- **Abgrenzung & Grenzen:** Ein [[Architekturstil]] ist nicht universell einsetzbar: Geschichtete [[Architektur|Architekturen]] eignen sich beispielsweise schlecht für hochdynamische Systeme mit häufigen [[Änderung|Änderungen]], während [[REST]]-basierte Stile bei stark gekoppelten [[Transaktion|Transaktionen]] an Grenzen stoßen. Alternativen wie [[Microservice|Microservices]] oder [[Event-Driven_Architecture|ereignisgesteuerte Architekturen]] können je nach [[Anforderung]] besser geeignet sein, verursachen jedoch oft höheren [[Koordinationsaufwand]] oder [[Komplexität]]. Monolithische [[Architektur|Architekturen]] bleiben bei kleinen Systemen oder spezifischen [[Performance]]-Anforderungen eine einfache Lösung, bieten aber weniger [[Flexibilität]] und [[Skalierbarkeit]]. Die Wahl des Stils sollte stets von den konkreten [[Anforderung|Anforderungen]] und [[Randbedingung|Randbedingungen]] des Systems abhängen.
- **Beispiel / Code:** ### Geschichteter [[Architekturstil]] am Beispiel eines HTTP-basierten Client-Server-Systems:

**Client (Anwendungsschicht, Layer 7):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.connect(('example.com', 80))
s.send(b'GET /data HTTP/1.1\r\nHost: example.com\r\n\r\n')
response = s.recv(1024)
print(response.decode())
s.close()
```
*Der Client sendet eine HTTP-Anfrage über eine TCP-Verbindung (Layer 4). Die Schichten abstrahieren die [[Kommunikation]] und ermöglichen eine klare Trennung der Verantwortlichkeiten.*

**Server (Anwendungsschicht, Layer 7):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('', 8080))
s.listen(1)
(conn, addr) = s.accept()
request = conn.recv(1024)
conn.send(b'HTTP/1.1 200 OK\r\nContent-Type: text/plain\r\n\r\nHello')
conn.close()
```
*Der Server verarbeitet die Anfrage auf Anwendungsebene und nutzt darunterliegende Schichten für [[Transport]] und [[Netzwerk]].*

### Beispiel für [[Request/Response]]-Kommunikation in einer geschichteten [[Architektur]]:

**Server (Layer N-1):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('', 8080))
s.listen(1)
(conn, addr) = s.accept()
data = conn.recv(1024)
conn.send(data + b'*')
conn.close()
```

**Client (Layer N):**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.connect(('localhost', 8080))
s.send(b'Hello')
print(s.recv(1024).decode())
s.close()
```
*Illustriert die [[Interaktion]] zwischen Schichten und die Standardisierung der [[Kommunikation]] durch definierte [[Schnittstelle|Schnittstellen]].*
