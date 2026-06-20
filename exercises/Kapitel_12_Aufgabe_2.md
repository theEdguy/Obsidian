---
id: eb922c29-7ed9-5d5a-91c5-9f321a96e026
title: "Kapitel_12_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - state_machine
  - trigger
  - exercise
  - draft
source: "Kapitel 12 Übung"
---

# Kapitel 12 Aufgabe 2

- **Aufgabenstellung:** Was gilt als 'Trigger' in einem Protokoll-Automaten?

A) Die Änderung eines Attributwerts in der Datenbank
B) Der Aufruf einer Systemoperation (z. B. login()), die im Protokoll definiert ist
C) Ein beliebiges asynchrones UI-Redraw-Event
D) Die Instanziierung einer Service-Klasse
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Im Protokoll-Automaten ist ein Trigger der Aufruf einer Systemoperation, der den Übergang von einem Protokollzustand in den nächsten auslösen kann.
- **Theoretischer Bezug:** [[Kapitel_12__Protokoll-Automaten]]
- **Stolpersteine / Fehlerquellen:** Verwechslung von allgemeinen Ereignissen (Events) mit den spezifischen Systemoperationsaufrufen (Triggern) des Protokolls.
