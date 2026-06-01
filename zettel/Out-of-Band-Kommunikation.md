---
id: f0bca214-e567-4955-af42-3d5c18f2cdce
title: "Out-of-Band-Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - server-architektur
  - netzwerkprotokolle
  - prozess-kommunikation
  - fehlerbehandlung
  - priorisierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Out-of-Band-Kommunikation]]

- **Kernkonzept:** Out-of-Band-Kommunikation bezeichnet die Übertragung von [[Daten|Daten]] oder [[Steuersignal|Steuersignalen]] über einen separaten [[Kommunikationskanal|Kommunikationskanäle]]n, um einen [[Server]] oder [[Prozess]] zu unterbrechen oder zu priorisieren, ohne den regulären [[Datenstrom]] zu blockieren.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]], dass [[Server]] oder [[Prozess|Prozesse]] während der Bearbeitung einer [[Anfrage]] unterbrochen werden müssen, z. B. für dringende [[Steuerungsbefehl|Steuerungsbefehle]] oder [[Fehlerbehandlung]]. Es ermöglicht [[Priorisierung]] und [[Echtzeitinteraktion]] ohne den Haupt-[[Datenstrom]] zu stören.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Systeme]], die keine [[Priorisierung]] benötigen oder bei denen [[Betriebssystem]]-Unterstützung für [[Thread]]- oder [[Prozess]]-Scheduling fehlt. Alternativen wie [[In-Band-Signalisierung]] (z. B. über TCP-Urgent-Flags) können einfacher sein, bieten aber weniger [[Isolation]] und [[Flexibilität]].
- **Beispiel / Code:** 1. **Separater Port für dringende Nachrichten (Lösung 1):**
```
// Server-seitiger Pseudocode
Thread normalHandler = new Thread(() -> handleNormalRequests());
Thread urgentHandler = new Thread(() -> handleUrgentRequests());
normalHandler.start();
urgentHandler.start();
```

2. **TCP-Urgent-Flag (Lösung 2):**
```c
// Client-seitiger C-Code (TCP)
send(socket, data, length, MSG_OOB); // Sendet dringende Daten
```

*Anmerkung: Beide Lösungen erfordern [[Betriebssystem]]- oder [[Protokoll]]-Unterstützung.*
