---
id: 567305ac-e466-4538-addd-4df6508ea4e9
title: "Parallelität_in_Zustandsmaschinen"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Parallelität_in_Zustandsmaschinen]]

- **Kernkonzept:** Die [[Parallelität_in_Zustandsmaschinen|Parallelität]] in [[Zustandsmaschine|Zustandsmaschinen]] ermöglicht die unabhängige Modellierung mehrerer [[Ablauf|Abläufe]] innerhalb eines [[Systems]], die gleichzeitig aktiv sein können, ohne sich gegenseitig zu blockieren.
- **Nutzen & Zweck:** Sie löst das Problem der Darstellung von [[Ablauf|Abläufen]], die unabhängig voneinander ablaufen (z. B. [[Labor|Labore]] und [[Vorlesung|Vorlesungen]] in einem [[Modul]]). Dadurch wird die [[Modularität]] erhöht und die [[Komplexität]] der [[Zustandsmaschine]] reduziert.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Ablauf|Abläufe]] stark voneinander abhängen oder synchronisiert werden müssen. In solchen Fällen ist eine explizite [[Synchronisierung]] oder ein [[Sequentieller_Ablauf]] vorzuziehen. Zudem erhöht [[Parallelität_in_Zustandsmaschinen|Parallelität]] die [[Komplexität]] der [[Implementierung]] und [[Testbarkeit]].
- **Beispiel / Code:** ```java
// Beispiel für parallele Zustände in einer hierarchischen Zustandsmaschine
public enum ParallelState {
    LABOR(LABOR_TEIL_1, LABOR_TEIL_2),
    VORLESUNG(VORLESUNG_BESUCHT);
    
    private List<State> subStates;
    
    ParallelState(State... subStates) {
        this.subStates = Arrays.asList(subStates);
    }
}
```
