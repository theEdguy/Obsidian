---
id: 60a04c64-7e49-48aa-b5b9-87f912a8be86
title: "Extend_Beziehung"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - requirements_engineering
  - use_case_modeling
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Extend_Beziehung]]

- **Kernkonzept:** Die <<extend>>-Beziehung in [[Use-Case-Diagramm|Use-Case-Diagrammen]] beschreibt, wie ein [[Use_Case|Use Case]] (der *erweiternde* [[Use_Case]]) einen anderen [[Use_Case]] (den *erweiterten* [[Use_Case]]) unter bestimmten [[Bedingung|Bedingungen]] oder an definierten [[Extension_Point|Extension Points]] um zusätzliche [[Ablauf|Abläufe]] ergänzt, ohne den [[Basis-Use-Case|Basis-Use-Case]] zu verändern.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung von [[optionale_Funktionalität|optionalen Funktionalitäten]], [[Variation|Variationen]] oder [[Ausnahmefall|Ausnahmefällen]] (z. B. [[Fehlerbehandlung]]), ohne den [[Hauptablauf]] des [[Basis-Use-Case|Basis-Use-Cases]] zu verkomplizieren. Dadurch bleibt die [[Kohäsion]] des [[Use_Case|Use Cases]] hoch, und [[Spezialfall|Spezialfälle]] werden klar von der [[Kernfunktionalität]] getrennt.
- **Abgrenzung & Grenzen:** Die <<extend>>-Beziehung ist nicht für [[obligatorische_Funktionalität|obligatorische Funktionalitäten]] oder [[Spezialisierung|Spezialisierungen]] geeignet. Hier sind [[Include-Beziehung|Include-Beziehungen]] oder [[Use_Case_Generalisierung|Use-Case-Generalisierungen]] vorzuziehen. Sie stellt keine zeitliche Abfolge dar und vererbt keine [[Beziehung|Beziehungen]] zu [[Akteur|Akteuren]]. Zudem sollte sie nicht verwendet werden, um [[Modularisierung|modulare]] [[Schnittstelle|Schnittstellen]] zu ersetzen, da dies die [[Wartbarkeit]] des Modells beeinträchtigen kann.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Mitglied as m

usecase "Mitglied löschen" as UC1
usecase "Daten archivieren" as UC2

m --> UC1
UC1 <.. UC2 : <<extend>>
note right on link
  Bedingung: [[Mitglied]] war länger als 5 Jahre aktiv
  [[Extension_Point|Extension Point]]: Vor Löschbestätigung
end note
@enduml
```

Im Beispiel erweitert der [[Use_Case]] *Daten archivieren* den [[Basis-Use-Case]] *Mitglied löschen* nur, wenn die [[Bedingung]] erfüllt ist und der [[Extension_Point]] erreicht wird.
