---
id: 525bd694-de85-47aa-bbe6-a23472e65a2b
title: "Use_Case_Generalisierung"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - uml
  - use_case_modeling
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Use_Case_Generalisierung]]

- **Kernkonzept:** Die [[Use_Case_Generalisierung]] beschreibt eine Beziehung zwischen [[Use_Case|Use Cases]], bei der ein [[Use_Case|Use Case]] „B“ einen Spezialfall eines allgemeineren [[Use_Case|Use Cases]] „A“ darstellt. „B“ erbt dabei alle [[Beziehung|Beziehungen]] von „A“.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung von [[Spezialisierung|Spezialisierungen]] in [[Anwendungsfall|Anwendungsfällen]], wenn der spezielle [[Use_Case|Use Case]] so eigenständig ist, dass er nicht durch [[Include-Beziehung|Include]]- oder [[Extend-Beziehung|Extend-Beziehungen]] adäquat abgebildet werden kann.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Spezialisierung]] lediglich eine Variation oder Erweiterung eines [[Basis-Use-Case|Basis-Use-Cases]] darstellt. In solchen Fällen sind [[Extend-Beziehung|Extend]] oder [[Include-Beziehung|Include]] vorzuziehen. Im Gegensatz zu [[Vererbung]] in der [[Objektorientierung]] werden keine [[Akteur|Akteure]] vererbt.
- **Beispiel / Code:** ```plantuml
@startuml
A <|-- B
A --> Cleo
B --> Cleo
@enduml
```
Hier ist „B“ ein spezialisierter [[Use_Case|Use Case]] von „A“, und beide sind mit dem [[Akteur|Akteur]] „Cleo“ assoziiert.
