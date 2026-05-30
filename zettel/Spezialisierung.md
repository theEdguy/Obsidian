---
id: df30fd88-9339-4ad0-bc50-0b3a560b71df
title: "Spezialisierung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Spezialisierung]]

- **Kernkonzept:** Die [[Spezialisierung]] ist eine Form der [[Vererbung]], bei der [[Unterklasse|Unterklassen]] spezifischere [[Eigenschaft|Eigenschaften]] oder [[Verhalten]] als ihre [[Oberklasse]] definieren. Die [[Instanz|Instanzen]] der [[Unterklasse]] bilden eine Teilmenge der [[Instanz|Instanzen]] der [[Oberklasse]].
- **Nutzen & Zweck:** Sie ermöglicht die Erweiterung oder Anpassung von [[Verhalten]] und [[Eigenschaft|Eigenschaften]] für spezifische Anwendungsfälle, ohne die [[Oberklasse]] zu verändern. Dies fördert die [[Modularität]] und [[Erweiterbarkeit]] von [[Software]].
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn keine spezifischen Anpassungen benötigt werden. Übermäßige [[Spezialisierung]] kann zu unnötiger Komplexität oder [[Code_Duplication|Code-Duplikation]] führen.
- **Beispiel / Code:** ```java
public class FitaTeam extends Team {
    @Override
    public int leistungsprognose(Date datum) {
        return 50; // Spezifische Implementierung
    }
}
```
