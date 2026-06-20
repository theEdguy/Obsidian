---
id: 8aefcbe9-cbac-5198-8fdb-5f63532414d2
title: "Kapitel_3_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - objektorientierung
  - identitaet
  - exercise
  - draft
source: "Kapitel 3 Übung"
---

# Kapitel 3 Aufgabe 1

- **Aufgabenstellung:** Gegeben sind in Java zwei Instanzen:
`String x = new String("text");` und `String y = new String("text");`.
Welches Ergebnis liefern die Ausdrücke `(x == y)` und `x.equals(y)`?

A) Beide liefern `true`.
B) Beide liefern `false`.
C) `(x == y)` liefert `true`, `x.equals(y)` liefert `false`.
D) `(x == y)` liefert `false`, `x.equals(y)` liefert `true`.
- **Lösungsweg / Musterlösung:** Richtige Antwort: D

Erklärung: Der Operator `==` prüft die Objektidentität (zeigen x und y auf denselben Speicherbereich?). Da beide mit `new` erzeugt wurden, sind sie unterschiedliche Objekte (false). Die Methode `equals()` prüft die inhaltliche Gleichheit (ist der Text derselbe?), was hier zutrifft (true).
- **Theoretischer Bezug:** [[Kapitel_3__Objektorientierung_–_eine_durchgängige_Sichtweise]]
- **Stolpersteine / Fehlerquellen:** Verwechslung von Identität (derselbe) und Gleichheit (der gleiche). Besondere Optimierungen wie String-Pooling in Java können bei Literalen (ohne 'new') verwirren.
