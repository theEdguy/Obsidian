---
id: 54ad68b2-5da0-4c4b-87eb-8d5e4dc59431
title: "Extend_Beziehung"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - requirements_engineering
  - use_case_modeling
  - variationen
  - draft
source: "software_engineering_kapitel_07"
---

# [[Extend_Beziehung]]

- **Kernkonzept:** Die <<extend>>-Beziehung in [[Use-Case-Diagramm|Use-Case-Diagrammen]] beschreibt, wie ein [[Use_Case|Use Case]] (der *erweiternde* [[Use_Case]]) einen anderen [[Use_Case]] (den *erweiterten* [[Use_Case]]) unter bestimmten [[Bedingung|Bedingungen]] oder an definierten [[Extension_Point|Extension Points]] um zusätzliche [[Ablauf|Abläufe]] ergänzt, ohne den [[Basis-Use-Case|Basis-Use-Case]] zu verändern. Sie modelliert [[optionale_Funktionalität|optionale Funktionalitäten]], [[Variation|Variationen]] oder [[Ausnahmefall|Ausnahmefälle]], die nur unter spezifischen Voraussetzungen ausgeführt werden.
- **Nutzen & Zweck:** Die <<extend>>-Beziehung löst das Problem, dass [[Use_Case|Use Cases]] oft [[Sonderfall|Sonderfälle]], [[optionale_Funktionalität|optionale Abläufe]] oder [[Ausnahmefall|Ausnahmefälle]] enthalten, die nicht immer auftreten, aber dennoch modelliert werden müssen. Sie ermöglicht eine klare Trennung zwischen dem [[Hauptablauf]] und seinen [[Variation|Variationen]], was die [[Übersichtlichkeit]] und [[Wartbarkeit]] des [[Modell|Modells]] erhöht. Dadurch bleibt die [[Kohäsion]] des [[Basis-Use-Case|Basis-Use-Cases]] hoch, und [[Spezialfall|Spezialfälle]] werden von der [[Kernfunktionalität]] isoliert, ohne diese zu verkomplizieren. Dies fördert die [[Modularisierung]] und unterstützt die [[Skalierbarkeit]] komplexer [[System|Systeme]], indem [[Erweiterbarkeit]] ohne strukturelle Änderungen am [[Basis-Use-Case]] erreicht wird.
- **Abgrenzung & Grenzen:** Die <<extend>>-Beziehung ist nicht für [[obligatorische_Funktionalität|obligatorische Funktionalitäten]] oder [[Spezialisierung|Spezialisierungen]] geeignet. Hier sind [[Include-Beziehung|Include-Beziehungen]] (für zwingend erforderliche [[Teilablauf|Teilabläufe]]) oder [[Use_Case_Generalisierung|Use-Case-Generalisierungen]] (für hierarchische [[Vererbung|Vererbungsstrukturen]]) vorzuziehen. Sie stellt keine zeitliche [[Abfolge]] dar und vererbt keine [[Beziehung|Beziehungen]] zu [[Akteur|Akteuren]], da sie keine [[Vererbungsrelation]] ist. Zudem sollte sie nicht verwendet werden, um [[Modularisierung|modulare]] [[Schnittstelle|Schnittstellen]] zu ersetzen, da dies die [[Wartbarkeit]] und [[Klarheit]] des [[Modell|Modells]] beeinträchtigen kann. Die Beziehung ist ungeeignet, wenn keine klaren [[Bedingung|Bedingungen]] oder [[Extension_Point|Extension Points]] definiert werden können, da dies zu unklaren oder inkonsistenten [[Modellierung|Modellierungen]] führt. Sie eignet sich auch nicht für die Darstellung von [[Workflow|Workflows]] oder [[Sequenz|Sequenzen]], da [[Use-Case-Diagramm|Use-Case-Diagramme]] keine [[Kontrollfluss|Kontrollflüsse]] abbilden.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Mitglied as m
actor Kunde as k

usecase "Mitglied löschen" as UC1
usecase "Daten archivieren" as UC2
usecase "Bestellung aufgeben" as UC3
usecase "Gutschein einlösen" as UC4

m --> UC1
UC2 <.. UC2 : <<extend>>
note right on link
  Bedingung: [[Mitglied]] war länger als 5 Jahre aktiv
  [[Extension_Point|Extension Point]]: Vor Löschbestätigung
end note

k --> UC3
UC4 .> UC3 : <<extend>>
note right on link
  Bedingung: Kunde hat Gutscheincode
  [[Extension_Point|Extension Point]]: Vor Zahlungsabschluss
end note
@enduml
```

**Erläuterung:**
- Im ersten Beispiel erweitert der [[Use_Case]] *Daten archivieren* den [[Basis-Use-Case]] *Mitglied löschen* nur, wenn die [[Bedingung]] (Mitglied war länger als 5 Jahre aktiv) erfüllt ist und der [[Extension_Point]] (Vor Löschbestätigung) erreicht wird.
- Im zweiten Beispiel wird der [[Basis-Use-Case]] *Bestellung aufgeben* durch *Gutschein einlösen* erweitert, falls der Kunde einen Gutscheincode besitzt. Die Erweiterung erfolgt am [[Extension_Point]] *Vor Zahlungsabschluss*. Beide Beispiele zeigen, wie [[optionale_Funktionalität|optionale Abläufe]] sauber vom [[Hauptablauf]] getrennt werden.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2
- **Vorgänger / Parent:** [[Use_Case_Beziehungen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Beziehungen]]
  - [[Variationen]]
