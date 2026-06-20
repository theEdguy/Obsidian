---
id: 4871c50a-80d4-52b7-93e4-c8fde12ce142
title: "Berkeley Sockets API"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Kommunikation"
---

# [[Berkeley Sockets API]]

- **Kernkonzept:** Systemnahe Abstraktionsebene für transiente Kommunikation. Server nutzt socket(), bind(), listen() und blockiert in accept() für Verbindungen. Client nutzt socket() und connect(). Datenaustausch erfolgt über send() und recv().
- **Nutzen & Zweck:** Systemnahe Abstraktionsebene für transiente Kommunikation. Server nutzt socket(), bind(), listen() und blockiert in accept() für Verbindungen. Client nutzt socket() und connect(). Datenaustausch erfolgt über send() und recv().
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# Server-Socket (Python):
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('localhost', 8080))
s.listen(1)
conn, addr = s.accept()
data = conn.recv(1024)
conn.send(data + b'*')
conn.close()
```
