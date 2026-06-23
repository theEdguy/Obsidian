---
id: 1692d9e1-846e-4ad8-8a82-68d89912e720
title: "Use Case Diagrammelemente"
date: 2026-06-23
tags:
  - software_engineering
  - elemente
  - diagramme
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Diagrammelemente]]

- **Kernkonzept:** Use-Case-Diagrammelemente sind grundlegende Bausteine der Unified Modeling Language (UML), die zur visuellen Darstellung von Akteuren, Use Cases, Systemgrenzen und deren Beziehungen in einem Softwaresystem dienen. Sie strukturieren funktionale Anforderungen aus Nutzerperspektive und zeigen Interaktionen zwischen Akteuren und dem System auf.
- **Nutzen & Zweck:** Use-Case-Diagrammelemente existieren, um die Kommunikation zwischen Stakeholdern zu vereinfachen und ein gemeinsames Verständnis der Systemanforderungen zu schaffen. Sie lösen das Problem der unklaren oder verstreuten Anforderungen, indem sie diese in übersichtliche, nutzerzentrierte Einheiten (Use Cases) gliedern und Abhängigkeiten sowie Prioritäten sichtbar machen. Dadurch bilden sie die Grundlage für Architekturentscheidungen, Testfälle und die iterative Entwicklung.
- **Abgrenzung & Grenzen:** Use-Case-Diagrammelemente sollten nicht genutzt werden, um technische Implementierungsdetails, zeitliche Abläufe oder nicht-funktionale Anforderungen detailliert abzubilden. Sie unterscheiden sich von Aktivitätsdiagrammen (die Workflows darstellen) oder Klassendiagrammen (die Systemstrukturen modellieren), da sie ausschließlich die funktionale Nutzerperspektive fokussieren. Zudem sind sie ungeeignet für Systeme mit minimaler Nutzerinteraktion oder rein datengetriebenen Prozessen, bei denen Akteure keine zentrale Rolle spielen.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Vereinsmanager
actor "Mail Client" as mail
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Mitglied löschen" as UC4
}

Vereinsmanager --> UC1
mail --> UC1
UC1 <|-- UC2
UC1 <|-- UC3
UC1 <|-- UC4
@enduml
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1f1
- **Vorgänger / Parent:** [[Use_Case_Diagramme]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Diagramme]]
  - [[UML]]
