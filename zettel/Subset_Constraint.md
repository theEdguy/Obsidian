---
id: 413d813b-5887-4bd4-8548-cc08ff390fda
title: "Subset_Constraint"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - datenintegrität
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Subset_Constraint]]

- **Kernkonzept:** Ein [[Subset_Constraint]] ist ein [[Constraint]], der sicherstellt, dass die [[Instanz|Instanzen]] einer [[Assoziation]] eine Teilmenge der [[Instanz|Instanzen]] einer anderen [[Assoziation]] sind.
- **Nutzen & Zweck:** Es ermöglicht die Modellierung von [[Hierarchie|hierarchischen Beziehungen]] oder [[Einschränkung|Einschränkungen]] zwischen [[Assoziation|Assoziationen]], um [[Datenkonsistenz]] zu gewährleisten.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Beziehung|Beziehungen]] unabhängig voneinander sind oder keine Teilmengenbeziehung besteht. Kann die [[Komplexität]] des [[Modell|Modells]] erhöhen.
- **Beispiel / Code:** ```java
class Mitglied {
    private List<Verein> teilDes;
    private Verein vorstand;
    // Vorstand muss Teilmenge von teilDes sein
}
```
