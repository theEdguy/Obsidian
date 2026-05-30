---
id: 66fd5c58-02b1-473f-a985-6b9c923acb6a
title: "Template_Klasse"
date: 2026-05-30
tags:
  - software_engineering
  - generics
  - datenstrukturen
  - entwurf
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Template_Klasse]]

- **Kernkonzept:** Eine [[Template_Klasse]] ist eine [[Klasse]] mit einem oder mehreren formalen Parametern, die eine Familie von [[Klasse|Klassen]] beschreibt. Durch [[Binding]] der Parameter entsteht eine konkrete [[Klasse]].
- **Nutzen & Zweck:** Sie ermöglicht die Definition generischer [[Datenstruktur|Datenstrukturen]] und [[Algorithmus|Algorithmen]], die unabhängig vom konkreten [[Datentyp]] sind. Dies fördert die [[Wiederverwendbarkeit]] und [[Typsicherheit]] im [[Code]].
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn der [[Datentyp]] bereits feststeht oder keine [[Generizität]] benötigt wird. [[Template_Klasse|Template-Klassen]] können die [[Komplexität]] des [[Code]]s erhöhen und sind nicht in allen [[Programmiersprache|Programmiersprachen]] verfügbar.
- **Beispiel / Code:** ```java
// Template-Klasse Set mit generischem Typ T
public class Set<T> {
    private List<T> elements = new ArrayList<>();
    
    public void addElem(T elem) {
        elements.add(elem);
    }
}

// Binding: Set<Mitglied> wird zu MitgliederSet
Set<Mitglied> mitgliederSet = new Set<>();
```
