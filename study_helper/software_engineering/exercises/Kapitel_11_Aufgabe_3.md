---
id: a5a462b3-0c08-5184-8122-bb3e6258206c
title: "Kapitel_11_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - mvc
  - initialisierung
  - sequenzdiagramm
  - exercise
  - draft
source: "Kapitel 11 Übung"
---

# Kapitel 11 Aufgabe 3

- **Aufgabenstellung:** Skizzieren Sie die Initialisierungsreihenfolge einer MVC-Anwendung mithilfe eines Sequenzdiagramms. Welche Objekte werden in welcher Reihenfolge erzeugt und wer registriert sich bei wem?
- **Lösungsweg / Musterlösung:** 1. Der Client/Starter erzeugt das Model `m = new Model()`.
2. Der Client erzeugt die View `v = new View(m)`. Im Konstruktor der View registriert sich die View beim Model als Observer: `m.attach(this)`.
3. Der Client erzeugt den Controller `c = new Controller(m, v)`.
4. Der Controller registriert sich bei der View für Benutzeraktionen (z. B. Button-Klicks).
5. Die Anwendung ist bereit.
- **Theoretischer Bezug:** [[Kapitel_11__MVC-Architektur_und_das_Observer-Muster]]
- **Stolpersteine / Fehlerquellen:** Die Annahme, der Controller erzeuge das Model. Das Model existiert unabhängig und wird in der Regel an View und Controller übergeben. Die View registriert sich beim Model als Observer, nicht umgekehrt.
