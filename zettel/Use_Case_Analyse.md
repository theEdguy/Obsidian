---
id: 0b54b1f7-1315-442e-ab64-1fdac35fd8d4
title: "Use_Case_Analyse"
date: 2026-05-30
tags:
  - software_engineering
  - anforderungsanalyse
  - modellierung
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Use_Case_Analyse]]

- **Kernkonzept:** Die [[Use_Case_Analyse]] identifiziert und priorisiert die zentralen [[Anwendungsfall|Anwendungsfälle]] eines Systems, um die [[Systemgrenze|Systemgrenzen]] und [[Akteur|Akteure]] zu definieren. Sie modelliert die Beziehungen zwischen [[Anwendungsfall|Anwendungsfällen]] in [[Use-Case-Diagramm|Use-Case-Diagrammen]].
- **Nutzen & Zweck:** Sie dient der strukturierten Erfassung von [[Anforderung|Anforderungen]] und der Fokussierung auf die kritischsten [[Anwendungsfall|Anwendungsfälle]], um das [[Problemverständnis]] zu schärfen und die [[Entwicklungsplanung]] zu steuern.
- **Abgrenzung & Grenzen:** Nicht geeignet für die detaillierte technische Umsetzung oder [[Architekturentscheidung|Architekturentscheidungen]]. Sie ersetzt keine [[Datenmodellierung]] oder [[Algorithmen|Algorithmen]]-Entwicklung. Im Gegensatz zu [[User_Story|User Stories]] ist sie formaler und stärker auf [[Systemgrenze|Systemgrenzen]] ausgerichtet.
- **Beispiel / Code:** ```plantuml
@startuml
actor Kunde
Kunde -> (Bestellung aufgeben)
Kunde -> (Zahlung durchführen)
(Bestellung aufgeben) .> (Zahlung durchführen) : <<includes>>
@enduml
```
