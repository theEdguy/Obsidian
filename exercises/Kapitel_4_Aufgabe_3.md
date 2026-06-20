---
id: 91f957c7-28dd-5570-ba42-7ee78fe0dd9a
title: "Kapitel_4_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - klassendiagramm
  - vererbung
  - interface
  - exercise
  - draft
source: "Kapitel 4 Übung"
---

# Kapitel 4 Aufgabe 3

- **Aufgabenstellung:** Stellen Sie das folgende Java-Codefragment als UML-Klassendiagramm dar:

```java
class B extends C implements D {
    @Override
    public void execute() {}
}
```
- **Lösungsweg / Musterlösung:** Das Klassendiagramm besteht aus:
1. Der Klasse `B` mit der Operation `execute()`.
2. Der Klasse `C`. `B` ist mit `C` über einen Pfeil mit durchgezogener Linie und nicht ausgefüllter Dreiecksspitze verbunden (Generalisierung/Vererbung: B -> C).
3. Dem Interface `D` (oder einer Klasse/Interface mit Stereotyp <<interface>>). `B` ist mit `D` über einen Pfeil mit gestrichelter Linie und nicht ausgefüllter Dreiecksspitze verbunden (Realisierung: B -> D).
- **Theoretischer Bezug:** [[Kapitel_4__Objektorientierung_–_Vererbung]]
- **Stolpersteine / Fehlerquellen:** Verwechslung der Pfeilspitzen oder Linienarten. Generalisierung ist eine durchgezogene Linie, Realisierung eines Interfaces ist gestrichelt. Beide nutzen eine geschlossene, nicht ausgefüllte Dreiecksspitze.
