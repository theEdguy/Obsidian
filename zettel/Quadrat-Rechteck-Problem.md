---
id: a0e7a61b-339a-41e1-a616-e948ae149d95
title: "Quadrat-Rechteck-Problem"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - design_problem
  - entwurfsmuster
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Quadrat-Rechteck-Problem]]

- **Kernkonzept:** Ein klassisches [[Designproblem]] in der [[Objektorientierung]], bei dem die [[Vererbung_(OOP)|Vererbung]] zwischen [[Quadrat]] und [[Rechteck]] zu Verletzungen des [[Substitutionsprinzips]] führt, da ein [[Quadrat]] nicht alle [[Eigenschaft|Eigenschaften]] eines [[Rechteck|Rechtecks]] erfüllt (z. B. unabhängige Seitenlängen).
- **Nutzen & Zweck:** Dient als [[Beispiel]] für die Grenzen der [[Vererbung_(OOP)|Vererbung]] und zeigt, wann [[Komposition]] oder andere [[Entwurfsmuster]] vorzuziehen sind. Hilft, [[Designfehler]] zu vermeiden, die durch falsche [[Ist-eine-Beziehung|„Ist-eine“-Beziehungen]] entstehen.
- **Abgrenzung & Grenzen:** Vererbung ist hier ungeeignet, da die [[Invariante]] eines [[Quadrat|Quadrats]] (`a == b`) die [[Invariante]] eines [[Rechteck|Rechtecks]] (`a != b` möglich) verletzt. Besser: [[Quadrat]] und [[Rechteck]] als separate [[Klasse|Klassen]] modellieren oder eine gemeinsame [[Schnittstelle]] verwenden.
- **Beispiel / Code:** ```java
// Problem: Verletzung des Substitutionsprinzips
Rechteck r = new Quadrat(5);
r.setA(4); // Setzt implizit auch b = 4 → bricht Rechteck-Invariante

// Lösung: Keine Vererbung, sondern Komposition oder Schnittstelle
interface Form {
    int flaeche();
}

class Rechteck implements Form { /* ... */ }
class Quadrat implements Form { /* ... */ }
```
