---
id: f0fe7494-0ec7-4fdc-adc7-73146541e377
title: "OSI-Referenzmodell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - architektur
  - protokolle
  - schichtenmodell
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[OSI-Referenzmodell]]

- **Kernkonzept:** Das OSI-Referenzmodell ist ein [[Schichtenmodell|geschichtetes]] [[Protokoll|Protokollmodell]], das die [[Kommunikation]] in [[verteilte Systeme|verteilten Systemen]] in sieben [[Abstraktionsebene|Abstraktionsebenen]] unterteilt, um [[Interoperabilität]] und [[Modularität]] zu gewährleisten.
- **Nutzen & Zweck:** Es standardisiert die [[Kommunikationsfunktion|Kommunikationsfunktionen]] in [[Netzwerk|Netzwerken]], um [[Komplexität]] zu reduzieren, [[Fehlerisolierung]] zu ermöglichen und die [[Entwicklung]] [[unabhängig|unabhängiger]] [[Protokoll|Protokolle]] für jede Schicht zu fördern. Dadurch wird die [[Integration]] verschiedener [[Hardware]]- und [[Software]]-Lösungen erleichtert.
- **Abgrenzung & Grenzen:** Das OSI-Modell ist ein theoretisches [[Referenzmodell]] und wird in der Praxis oft durch das [[TCP/IP-Modell]] ersetzt, das weniger Schichten hat und direkt auf [[Internet]]-Technologien zugeschnitten ist. Es eignet sich nicht für [[Echtzeitkommunikation|Echtzeitanwendungen]] oder [[Middleware]]-basierte [[Systeme]], die höhere [[Abstraktionsebenen]] benötigen. Zudem kann die strikte Schichtenarchitektur zu [[Overhead]] führen.
- **Beispiel / Code:** ```
// Beispiel: Aufbau einer TCP-Verbindung (Transportschicht, OSI-Layer 4)
// Client-seitiger Pseudocode
Socket clientSocket = new Socket("server.example.com", 8080);
OutputStream out = clientSocket.getOutputStream();
out.write("Hello, Server!".getBytes());
```

*Erläuterung*: Die Transportschicht (Layer 4) nutzt [[TCP]] für [[verbindungsorientierte]] [[Kommunikation]], während die darunterliegenden Schichten (z. B. IP auf Layer 3) für [[Routing]] und [[Adressierung]] zuständig sind.
