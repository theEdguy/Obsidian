---
id: 0c9cb0c6-f18c-5edc-8523-736cf6eaa768
title: "Kapitel_5_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - klassendiagramm
  - qualifier
  - assoziationsklasse
  - exercise
  - draft
source: "Kapitel 5 Übung"
---

# Kapitel 5 Aufgabe 2

- **Aufgabenstellung:** Zeichnen Sie ein UML-Klassendiagramm für folgendes Szenario:
Ein Hotel hat Zimmer. Gäste können Zimmer reservieren. Für jede Reservierung wird der Zeitraum (von, bis) festgehalten. Ein Gast kann mehrere Reservierungen haben. Um die Suche nach Zimmern zu beschleunigen, wird an der Klasse Hotel ein Qualifier 'zimmerNummer' verwendet.
- **Lösungsweg / Musterlösung:** Das Diagramm enthält:
1. Klassen `Hotel`, `Zimmer` und `Gast`.
2. Eine Assoziation zwischen `Hotel` und `Zimmer`. Am Hotel-Ende ist ein Qualifier-Kästchen mit dem Attribut `zimmerNummer: int` angebracht. Am Zimmer-Ende ist die Multiplizität `0..1` (da eine Zimmernummer in einem Hotel eindeutig ein Zimmer bestimmt), am Hotel-Ende `1`.
3. Eine Assoziation zwischen `Gast` und `Zimmer` mit der Assoziationsklasse `Reservierung`, welche die Attribute `von: Date` und `bis: Date` enthält.
- **Theoretischer Bezug:** [[Kapitel_5__Objektorientierung_–_Komposition,_Aggregation_und_Assoziation]]
- **Stolpersteine / Fehlerquellen:** Falsche Platzierung des Qualifiers: Er gehört an die Quellklasse (Hotel), die den Index hält, nicht an die Zielklasse. Falsches Zeichnen der Assoziationsklasse (sie wird mit einer gestrichelten Linie an die Assoziationslinie gehängt, nicht direkt verbunden).
