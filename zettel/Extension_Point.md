---
id: e97aa350-6715-450d-b6fc-a137e54f04f5
title: "Extension_Point"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - uml
  - use_case_modeling
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Extension_Point]]

- **Kernkonzept:** Ein [[Extension_Point]] ist ein definierter Punkt in einem [[Basis-Use-Case|Basis-Use-Case]], an dem eine [[Extend-Beziehung|Extend-Beziehung]] ansetzen kann, um den [[Use_Case|Use Case]] zu erweitern.
- **Nutzen & Zweck:** Er ermöglicht die präzise Definition von Stellen, an denen [[Variation|Variationen]] oder [[Erweiterung|Erweiterungen]] in einem [[Anwendungsfall]] auftreten können, ohne den [[Basis-Use-Case|Basis-Use-Case]] zu verändern.
- **Abgrenzung & Grenzen:** Nicht relevant für [[Include-Beziehung|Include-Beziehungen]] oder [[Use_Case_Generalisierung|Generalisierungen]], da diese keine optionalen [[Erweiterung|Erweiterungen]] darstellen.
- **Beispiel / Code:** ```plantuml
@startuml
A --> (Extension Point) : <<extend>>
B --> (Extension Point)
@enduml
```
Hier ist „Extension Point“ der Punkt, an dem „B“ den [[Use_Case|Use Case]] „A“ erweitert.
