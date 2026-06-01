---
id: b7f2ef73-a322-405d-ba7a-3cb7daef948f
title: "Dreischicht-Modell (Three-Tier Architecture)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - server-cluster
  - cloud-computing
  - software-design
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Dreischicht-Modell (Three-Tier Architecture)]]

- **Kernkonzept:** Das Dreischicht-Modell [[Architekturmuster|Architekturmuster]] strukturiert verteilte [[System|Systeme]] in drei logische [[Schicht|Schichten]]: Präsentation (Client), Anwendung (Logik) und Datenhaltung (Server). Es trennt Verantwortlichkeiten und ermöglicht skalierbare [[Lösung|Lösungen]].
- **Nutzen & Zweck:** Es löst das Problem der [[Skalierbarkeit|Skalierbarkeit]], [[Wartbarkeit|Wartbarkeit]] und [[Flexibilität|Flexibilität]] in verteilten [[System|Systemen]], indem es klare Schnittstellen zwischen [[Schicht|Schichten]] definiert und die [[Lastverteilung|Lastverteilung]] optimiert. Besonders nützlich in [[Cloud-Computing|Cloud-Umgebungen]] und [[Server-Cluster|Server-Clustern]].
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]] mit geringer Komplexität, da der Overhead der [[Schicht|Schichten]]-Trennung unnötig ist. Unterscheidet sich von [[Zweischichtmodell|Zweischichtmodellen]] (Client-Server) durch die zusätzliche Trennung von Logik und Datenhaltung. Bei [[Echtzeit-System|Echtzeit-Systemen]] kann die Latenz durch die [[Schicht|Schichten]]-Kommunikation problematisch sein.
- **Beispiel / Code:** Ein typischer Aufbau in einem Web-System:
1. **Präsentationsschicht**: Webbrowser (HTML/CSS/JavaScript)
2. **Anwendungsschicht**: Applikationsserver (z. B. Node.js oder Java Spring)
3. **Datenhaltungsschicht**: Datenbankserver (z. B. PostgreSQL oder MongoDB)

Beispiel für Request-Verarbeitung:
- Client sendet HTTP-Request an den Load Balancer (1. Schicht).
- Load Balancer leitet Request an einen Applikationsserver (2. Schicht) weiter.
- Applikationsserver verarbeitet die Logik und greift auf die Datenbank (3. Schicht) zu.
- Antwort wird über die Schichten zurück an den Client gesendet.
