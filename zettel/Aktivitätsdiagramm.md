---
id: a29a1904-55a9-403e-8341-644ac6166959
title: "Aktivitätsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - workflow
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Aktivitätsdiagramm]]

- **Kernkonzept:** Ein [[Aktivitätsdiagramm]] ist ein [[UML-Diagramm]], das [[Ablauf|Abläufe]] beliebiger Granularität durch [[Aktion|Aktionen]], [[Transition|Transitionen]], [[Entscheidung|Entscheidungen]] und [[Parallelität|parallele Pfade]] modelliert.
- **Nutzen & Zweck:** Es dient der Visualisierung von [[Geschäftsprozess|Geschäftsprozessen]], [[Algorithmus|Algorithmen]], [[Workflows]] oder [[Anwendungsfall|Anwendungsfällen]] und hilft, komplexe [[Ablauf|Abläufe]] zu verstehen und zu kommunizieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung von [[Zustandsübergang|Zustandsübergängen]] oder [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]]. Hier sind [[Zustandsdiagramm|Zustandsdiagramme]] oder [[Sequenzdiagramm|Sequenzdiagramme]] vorzuziehen.
- **Beispiel / Code:** ```plantuml
@startuml
start
:Datum und Motto festlegen;
if (Budget ausreichend?) then (ja)
  :Gästeliste zusammenstellen;
else (nein)
  :Sponsoren finden;
endif
stop
@enduml
```
