---
id: 9360e1ea-938d-4853-8393-78d41f31c1ec
title: "Ist-eine-Beziehung"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - design_prinzipien
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Ist-eine-Beziehung]]

- **Kernkonzept:** Eine [[Beziehung]] in der [[Objektorientierung]], bei der eine [[Unterklasse]] eine spezielle Form ihrer [[Oberklasse]] darstellt und deren [[Eigenschaft|Eigenschaften]] und [[Verhalten]] erbt. Wird oft als „[[Vererbung_(OOP)|Vererbung]]“ modelliert.
- **Nutzen & Zweck:** Ermöglicht die Modellierung hierarchischer [[Struktur|Strukturen]] und fördert die [[Wiederverwendung]] von [[Code]]. Unterstützt das [[Substitutionsprinzip]], sodass [[Unterklasse|Unterklassen]] als [[Oberklasse|Oberklassen]] behandelt werden können.
- **Abgrenzung & Grenzen:** Sollte nur verwendet werden, wenn die [[Beziehung]] semantisch korrekt ist (z. B. „Ein [[Spieler]] ist ein [[Mitglied]]“). Falsche Anwendung führt zu [[Designfehler|Designfehlern]], wie im [[Quadrat-Rechteck-Problem]]. Alternativen wie [[Komposition]] sind oft besser geeignet.
- **Beispiel / Code:** ```java
// Korrekte „Ist-eine“-Beziehung
class Mitglied { /* ... */ }
class Spieler extends Mitglied { /* ... */ } // Spieler IST ein Mitglied

// Falsche „Ist-eine“-Beziehung
class Rechteck { /* ... */ }
class Quadrat extends Rechteck { /* ... */ } // Quadrat IST KEIN Rechteck (semantisch fragwürdig)
```
