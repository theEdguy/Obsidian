---
id: c22ccab0-07ad-44e5-89be-7908cb8f3676
title: "Generalisierung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Generalisierung]]

- **Kernkonzept:** Die [[Generalisierung]] beschreibt die Beziehung zwischen einer [[Oberklasse]] und ihren [[Unterklasse|Unterklassen]], bei der gemeinsame [[Eigenschaft|Eigenschaften]] und [[Verhalten]] in der [[Oberklasse]] zusammengefasst werden. Sie ist ein zentrales Konzept der [[Vererbung]].
- **Nutzen & Zweck:** Sie reduziert [[Redundanz]] und fördert die [[Wiederverwendbarkeit]] von [[Code]] durch die Definition gemeinsamer [[Schnittstelle|Schnittstellen]] und [[Verhalten]] in der [[Oberklasse]]. Dies erleichtert die [[Erweiterbarkeit]] und [[Wartbarkeit]] von [[Software]].
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn [[Unterklasse|Unterklassen]] keine gemeinsamen [[Eigenschaft|Eigenschaften]] oder [[Verhalten]] teilen. Übermäßige [[Generalisierung]] kann zu unnötiger Komplexität oder [[Fragile_Base_Class_Problem|fragilen Basisklassen]] führen.
- **Beispiel / Code:** ```java
// Generalisierung: Team als Oberklasse
public abstract class Team {
    protected String name;
    
    public abstract int leistungsprognose(Date datum);
}

// Spezialisierung: DDDTeam als Unterklasse
public class DDDTeam extends Team {
    @Override
    public int leistungsprognose(Date datum) {
        return 42;
    }
}
```
