---
id: 8a2e5945-62a9-492f-8a1e-4621ccc31bc8
title: "Port (Netzwerk)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - protokolle
  - kommunikation
  - transportschicht
  - server
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Port (Netzwerk)]]

- **Kernkonzept:** Ein [[Port|Port]] ist eine logische [[Adresse|Adressierung]] innerhalb eines [[Netzwerkprotokoll|Netzwerkprotokolls]], die es ermöglicht, [[Dienst|Dienste]] auf einem [[Rechner]] eindeutig zu identifizieren und [[Kommunikation]] zwischen [[Prozess|Prozessen]] zu koordinieren.
- **Nutzen & Zweck:** Ein [[Port]] löst das Problem der [[Mehrdeutigkeit]] bei der [[Kommunikation]] zwischen [[Prozess|Prozessen]] auf einem oder mehreren [[Rechner|Rechnern]]. Er ermöglicht die [[Zuordnung]] von [[Netzwerkverkehr]] zu spezifischen [[Dienst|Diensten]] oder [[Anwendung|Anwendungen]], z. B. [[Webserver]], [[E-Mail]]- oder [[Dateiübertragung|Dateiübertragungsdiensten]]. Ohne [[Port|Ports]] wäre eine [[parallele]] Nutzung mehrerer [[Dienst|Dienste]] auf einem [[Rechner]] nicht möglich.
- **Abgrenzung & Grenzen:** [[Port|Ports]] sollten nicht mit [[physikalischen]] Anschlüssen (z. B. USB-Ports) verwechselt werden. Sie sind rein logische Konstrukte der [[Transportschicht]] (z. B. TCP/UDP). Alternativen wie [[Named Pipes]] oder [[Unix Domain Sockets]] eignen sich nur für [[lokale]] [[Interprozesskommunikation]], während [[Port|Ports]] für [[netzwerkweite]] [[Kommunikation]] konzipiert sind. Bei [[hochsicheren]] Systemen können [[Port|Ports]] ein [[Angriffsvektor]] sein, wenn sie nicht durch [[Firewall|Firewalls]] oder [[Zugriffskontrolle|Zugriffskontrollen]] geschützt werden.
- **Beispiel / Code:** Ein typisches Beispiel ist die Nutzung von [[Port]] 80 für [[HTTP]]-Anfragen an einen [[Webserver]]:

```
// Client-seitiger Code (Python) zum Abrufen einer Webseite
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect(('example.com', 80))  // Port 80 für HTTP
client.send(b'GET / HTTP/1.1\r\nHost: example.com\r\n\r\n')
response = client.recv(4096)
print(response.decode())
client.close()
```

Standardisierte [[Port|Ports]] (0–1023) sind für [[Systemdienst|Systemdienste]] reserviert, während [[Anwendung|Anwendungen]] dynamische [[Port|Ports]] (1024–65535) nutzen können.
