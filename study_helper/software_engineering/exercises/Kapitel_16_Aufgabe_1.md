---
id: f46ecef9-a1e7-558c-9940-3c78f7ddcd91
title: "Kapitel_16_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - persistenz
  - concurrency
  - orm
  - exercise
  - draft
source: "Kapitel 16 Übung"
---

# Kapitel 16 Aufgabe 1

- **Aufgabenstellung:** Warum sollte beim Einsatz von OR-Mappern wie Hibernate der Datenbankzugriff nicht aus mehreren parallelen Threads auf derselben Session durchgeführt werden?

A) Weil relationale Datenbanken generell keine parallelen Anfragen unterstützen.
B) Um Probleme mit Datenbank-Locks und inkonsistenten Zuständen (Race Conditions) innerhalb des Session-Kontextes zu vermeiden.
C) Weil OR-Mapper keine Multi-Thread-Anwendungen erlauben.
D) Um den Arbeitsspeicher des Client-Rechners zu schonen.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: OR-Mapper verwalten geladene Objekte in einem Session-Kontext (First-Level Cache). Greifen mehrere Threads gleichzeitig auf diese Session zu, kommt es zu Race Conditions und Synchronisationskonflikten (Locks). Datenbankzugriffe müssen daher thread-safe koordiniert werden.
- **Theoretischer Bezug:** [[Kapitel_16__GUI-Anbindung_und_Persistenz]]
- **Stolpersteine / Fehlerquellen:** Die falsche Annahme, dass relationale Datenbanken an sich keine Nebenläufigkeit unterstützen (das tun sie auf Server-Ebene, aber nicht die clientseitige ORM-Session).
