---
id: 14f0046e-e55b-52ee-be5f-65d7ec1debe1
title: "Kapitel_11_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - mvc
  - observer
  - exercise
  - draft
source: "Kapitel 11 Übung"
---

# Kapitel 11 Aufgabe 1

- **Aufgabenstellung:** Welche Komponente im MVC-Pattern übernimmt typischerweise die Rolle des Subjekts im Observer-Muster?

A) Die View
B) Der Controller
C) Das Model
D) Die Zustandsmaschine
- **Lösungsweg / Musterlösung:** Richtige Antwort: C

Erklärung: Das Model verwaltet die Daten und den Zustand der Anwendung. Es fungiert als Subjekt und bietet Schnittstellen wie attach(Observer), um Views und Controller über Zustandsänderungen zu informieren, damit sich diese synchronisieren.
- **Theoretischer Bezug:** [[Kapitel_11__MVC-Architektur_und_das_Observer-Muster]]
- **Stolpersteine / Fehlerquellen:** Falsche Zuweisung des Subjekts an den Controller (der Eingaben steuert, aber keine Daten verwaltet) oder an die View.
