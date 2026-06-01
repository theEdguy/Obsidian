---
id: 91b50661-9d47-4c47-800a-c557a5229376
title: "Methodenaufruf (Remote Procedure Call, RPC)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - kommunikation
  - protokoll
  - client-server
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Methodenaufruf (Remote Procedure Call, RPC)]]

- **Kernkonzept:** Ein [[Methodenaufruf|Methodenaufrufe]] (RPC) ermöglicht die Ausführung von [[Prozedur|Prozeduren]] auf entfernten [[System|Systemen]], als wären sie lokal verfügbar, und abstrahiert dabei die Komplexität der [[Netzwerkkommunikation]].
- **Nutzen & Zweck:** RPC löst das [[Problem]] der [[Verteilung]] von [[Logik]] in [[verteilten Systemen]], indem es [[Transparenz]] für [[Aufruf|Aufrufe]] über [[Netzwerk]]-Grenzen hinweg schafft. Es vereinfacht die [[Entwicklung]] von [[Client-Server]]-Anwendungen durch [[Abstraktion]] der [[Kommunikation]].
- **Abgrenzung & Grenzen:** RPC ist ungeeignet für [[szenario|Szenarien]] mit hoher [[Latenz]]-Empfindlichkeit oder [[asynchroner]] Verarbeitung. Alternativen wie [[Messaging]] oder [[REST]]-basierte [[Schnittstelle|Schnittstellen]] bieten mehr [[Flexibilität]] bei [[zustandsloser]] Kommunikation. RPC kann [[Overhead]] durch [[Serialisierung]] und [[Netzwerk]]-Protokolle verursachen.
- **Beispiel / Code:** Ein einfaches RPC-Beispiel in Python mit dem `xmlrpc`-Modul:

**Server:**
```python
from xmlrpc.server import SimpleXMLRPCServer

def add(a, b):
    return a + b

server = SimpleXMLRPCServer(('localhost', 8000))
server.register_function(add, 'add')
server.serve_forever()
```

**Client:**
```python
import xmlrpc.client

proxy = xmlrpc.client.ServerProxy('http://localhost:8000/')
result = proxy.add(5, 3)
print(result)  # Ausgabe: 8
```
