---
id: 69f11b21-c034-5109-8014-857a85a080f2
title: "Kapitel_4_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - objektorientierung
  - liskov
  - vererbung
  - exercise
  - draft
source: "Kapitel 4 Übung"
---

# Kapitel 4 Aufgabe 1

- **Aufgabenstellung:** Warum ist die Vererbung `Quadrat erbt von Rechteck` im Sinne des Liskovschen Substitutionsprinzips problematisch?

A) Weil ein Quadrat geometrisch kein Rechteck ist.
B) Weil Operationen des Rechtecks wie `stretch(width, height)` oder unabhängige Setter die Invariante des Quadrats (Breite = Höhe) verletzen.
C) Weil Java keine Mehrfachvererbung unterstützt.
D) Weil das Quadrat weniger Attribute als das Rechteck benötigt.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Das Substitutionsprinzip verlangt, dass ein Quadrat überall dort verwendet werden kann, wo ein Rechteck erwartet wird. Wenn ein Client auf einem Rechteck-Objekt die Breite und Höhe unabhängig voneinander ändert (z.B. setBreite(4), setHoehe(5)), bricht diese Logik bei einem Quadrat zusammen, da sich dessen Invariante (w == h) nicht aufrechterhalten lässt, ohne das Verhalten der Oberklasse zu verfälschen.
- **Theoretischer Bezug:** [[Kapitel_4__Objektorientierung_–_Vererbung]]
- **Stolpersteine / Fehlerquellen:** Umgangssprachliches Denken ('Ein Quadrat ist doch ein Rechteck') kollidiert hier mit der Verhaltenskompatibilität im Softwaredesign.
