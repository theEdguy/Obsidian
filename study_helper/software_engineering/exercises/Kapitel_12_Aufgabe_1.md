---
id: a1b817c6-a91a-51b2-a2d6-bb30f9ea6e25
title: "Kapitel_12_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - state_machine
  - protokoll_automat
  - exercise
  - draft
source: "Kapitel 12 Übung"
---

# Kapitel 12 Aufgabe 1

- **Aufgabenstellung:** Welche Aussage beschreibt korrekt die Rolle von Vor- und Nachbedingungen in einem Protokoll-Automaten?

A) Vorbedingungen definieren die Zustände nach einer Operation, Nachbedingungen die Zustände davor.
B) Vorbedingungen spezifizieren die Menge der Zustände, in denen ein Aufruf einer Systemoperation zulässig ist, Nachbedingungen den Zustand nach Abschluss der Operation.
C) Beide Bedingungen sind optional und dienen nur der Entwickler-Dokumentation.
D) Vor- und Nachbedingungen legen ausschließlich die GUI-Aktivität fest.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Vorbedingungen legen fest, wann ein API-Aufruf oder eine Systemoperation valide ist. Nachbedingungen sichern zu, in welchen Zustand das System nach der Ausführung übergeht.
- **Theoretischer Bezug:** [[Kapitel_12__Protokoll-Automaten]]
- **Stolpersteine / Fehlerquellen:** Vertauschen von Vor- und Nachbedingung oder Geringschätzung ihrer formalen Bedeutung für die Zustandskonsistenz.
