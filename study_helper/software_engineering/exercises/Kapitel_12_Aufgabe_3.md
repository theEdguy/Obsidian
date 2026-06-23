---
id: 5f767800-a6b6-5532-88a2-90b9f1b79210
title: "Kapitel_12_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - zustandsdiagramm
  - history_state
  - exercise
  - draft
source: "Kapitel 12 Übung"
---

# Kapitel 12 Aufgabe 3

- **Aufgabenstellung:** Erklären Sie anhand einer Skizze oder Beschreibung den Unterschied zwischen einem flachen History-Zustand (H) und einem tiefen History-Zustand (H*).
- **Lösungsweg / Musterlösung:** - Flacher History-Zustand (H): Speichert nur den Zustand auf der aktuellen Verschachtelungsebene des zusammengesetzten Zustands. Unterzustände von Unterzuständen werden beim Wiedereintritt auf ihre jeweiligen Default-Startzustände zurückgesetzt.
- Tiefer History-Zustand (H*): Speichert rekursiv alle aktiven Unterzustände über alle Verschachtelungsebenen hinweg und stellt den exakten Zustand beim Wiedereintritt wieder her.
- **Theoretischer Bezug:** [[Kapitel_12__Protokoll-Automaten]]
- **Stolpersteine / Fehlerquellen:** Verwechslung von H und H*. Falsche Annahme, dass der flache History-Zustand beliebig tief speichert.
