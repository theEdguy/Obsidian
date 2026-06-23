---
id: acb5e0c7-80b8-5f24-92f7-f04debae9b61
title: "Kapitel_5_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - objektorientierung
  - beziehungen
  - komposition
  - exercise
  - draft
source: "Kapitel 5 Übung"
---

# Kapitel 5 Aufgabe 1

- **Aufgabenstellung:** Welche Aussage beschreibt den Unterschied zwischen einer Aggregation und einer Komposition in UML korrekt?

A) Bei der Aggregation können Teile nicht ohne das Ganze existieren, bei der Komposition schon.
B) Die Komposition ist eine exklusive Besitzbeziehung mit Existenzabhängigkeit (Teil stirbt mit dem Ganzen); bei der Aggregation können Teile unabhängig existieren.
C) Aggregations-Teile werden immer zur Compilezeit erzeugt, Kompositions-Teile zur Laufzeit.
D) Komposition wird durch eine leere Raute dargestellt, Aggregation durch eine gefüllte Raute.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Bei der Komposition (gefüllte Raute) liegt eine starke Existenzabhängigkeit vor. Das Ganze steuert den Lebenszyklus der Teile. Bei der Aggregation (leere Raute) handelt es sich um eine lose Kopplung; die Teile existieren unabhängig weiter, wenn das Aggregat zerstört wird (z. B. ein Buch im Bücherregal).
- **Theoretischer Bezug:** [[Kapitel_5__Objektorientierung_–_Komposition,_Aggregation_und_Assoziation]]
- **Stolpersteine / Fehlerquellen:** Verwechslung der Rauten (gefüllt = Komposition/stark, leer = Aggregation/schwach) und Missinterpretation der Lebenszyklus-Verantwortlichkeiten.
