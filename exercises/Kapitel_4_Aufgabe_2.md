---
id: 37aeb6ae-e6b5-50e1-87fe-2c762e9ceba3
title: "Kapitel_4_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - metamodellierung
  - mof
  - exercise
  - draft
source: "Kapitel 4 Übung"
---

# Kapitel 4 Aufgabe 2

- **Aufgabenstellung:** Ordne die UML-Modellierungsebene einer konkreten Klasse (z.B. 'class Mitglied') und einer konkreten Instanz zur Laufzeit (z.B. 'new Mitglied("Meier")') den korrekten Schichten der MOF-Architektur (Meta Object Facility) zu.

A) Klasse = M3, Instanz = M2
B) Klasse = M2, Instanz = M1
C) Klasse = M1, Instanz = M0
D) Klasse = M2, Instanz = M0
- **Lösungsweg / Musterlösung:** Richtige Antwort: C

Erklärung: In der MOF-Architektur ist M1 die Modell-Ebene (wo wir Klassen wie 'Mitglied' modellieren). M0 ist die Laufzeit-Ebene mit den realen Objekten im Speicher ('Meier'). M2 enthält das Meta-Modell (die UML-Definition von 'Class' und 'Attribute'), und M3 ist das Meta-Meta-Modell.
- **Theoretischer Bezug:** [[Kapitel_4__Objektorientierung_–_Vererbung]]
- **Stolpersteine / Fehlerquellen:** Verwechslung der Klassendefinition (M1) mit dem UML-Metamodell (M2).
