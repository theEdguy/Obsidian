---
id: f2b94c18-e5ed-4997-9371-a613b6d6ec4f
title: "Binäre_Assoziation"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Binäre_Assoziation]]

- **Kernkonzept:** Eine [[Binäre_Assoziation|binäre Assoziation]] beschreibt eine Beziehung zwischen den [[Instanz|Instanzen]] zweier [[Klasse|Klassen]], wobei jedes [[Assoziationsende]] spezifische Eigenschaften wie [[Stelligkeit]], [[Rolle|Rollenbezeichner]] und [[Navigierbarkeit]] besitzen kann.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung von [[Beziehung|Beziehungen]] zwischen [[Objekt|Objekten]] in [[Objektorientierte_Programmierung|objektorientierten Systemen]], um strukturelle Abhängigkeiten und [[Datenmodellierung|Datenmodelle]] klar abzubilden.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Mehrstellige_Assoziation|mehrstellige Beziehungen]] oder Fälle, in denen zusätzliche [[Attribut|Attribute]] oder [[Operation|Operationen]] direkt der [[Beziehung]] zugeordnet werden müssen. Hier sind [[Assoziationsklasse|Assoziationsklassen]] oder [[Mehrstellige_Assoziation|mehrstellige Assoziationen]] vorzuziehen.
- **Beispiel / Code:** ```java
class Verein {
    private List<Mitglied> mitglieder;
}

class Mitglied {
    // Navigierbar nur in eine Richtung
}
```
