---
id: 42950917-3b99-4b3f-8a3b-ddcd012a5a12
title: "Split_und_Join"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - parallelverarbeitung
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Split_und_Join]]

- **Kernkonzept:** [[Split_und_Join]] sind Mechanismen in [[Aktivitätsdiagramm|Aktivitätsdiagrammen]], um [[Parallelität|parallele Pfade]] zu erzeugen ([[Split]]) und wieder zusammenzuführen ([[Join]]).
- **Nutzen & Zweck:** Sie ermöglichen die Modellierung von [[Nebenläufigkeit|nebenläufigen Abläufen]] und [[Parallelverarbeitung|parallelen Prozessen]], um komplexe [[Workflows]] oder [[Algorithmus|Algorithmen]] abzubilden.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung von [[Sequenz|sequenziellen Abläufen]] oder [[Entscheidung|Entscheidungen]]. Hier sind [[Transition|Transitionen]] oder [[Entscheidungsknoten]] vorzuziehen.
- **Beispiel / Code:** ```plantuml
@startuml
start
split
  :Aktion 1;
  :Aktion 2;
split again
  :Aktion 3;
end split
:Zusammenführung;
stop
@enduml
```
