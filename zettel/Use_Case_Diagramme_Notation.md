---
id: e2a5c24d-c00b-4210-8763-376c4e5cdf48
title: "Use Case Diagramme Notation"
date: 2026-06-23
tags:
  - software_engineering
  - notation
  - diagramme
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Diagramme Notation]]

- **Kernkonzept:** Use-Case-Diagramme sind eine grafische Notation der Unified Modeling Language (UML), die Akteure, Use Cases und deren Beziehungen innerhalb eines Systems darstellen, um funktionale Anforderungen aus Benutzersicht zu modellieren.
- **Nutzen & Zweck:** Use-Case-Diagramme dienen dazu, die Interaktionen zwischen externen Akteuren und einem System übersichtlich zu strukturieren. Sie lösen das Problem, komplexe Anforderungen frühzeitig zu erfassen, zu priorisieren und für alle Projektbeteiligten verständlich zu kommunizieren, um eine gemeinsame Basis für Architektur, Design und Implementierung zu schaffen.
- **Abgrenzung & Grenzen:** Use-Case-Diagramme sollten nicht genutzt werden, um technische Details, zeitliche Abläufe oder nicht-funktionale Anforderungen detailliert abzubilden. Sie unterscheiden sich von Aktivitätsdiagrammen (die Prozesse abbilden) oder Klassendiagrammen (die statische Strukturen zeigen), da sie ausschließlich die funktionale Außensicht des Systems aus Benutzerperspektive darstellen. Für Workflows oder interne Systemlogik sind andere UML-Diagramme besser geeignet.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Vereinsmanager
actor MailClient
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Abteilungswechsel melden" as UC4
}

Vereinsmanager --> UC1
Vereinsmanager --> UC2
Vereinsmanager --> UC3
UC1 <|-- UC2
UC1 <|-- UC3
UC3 --> UC4
MailClient --> UC4
@enduml
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1f2
- **Vorgänger / Parent:** [[Use_Case_Diagramme]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Diagramme]]
  - [[UML]]
