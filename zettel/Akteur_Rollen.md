---
id: e9e9462e-d5a4-4347-95e2-4b0952311094
title: "Akteur Rollen"
date: 2026-06-23
tags:
  - software_engineering
  - rollen
  - akteure
  - draft
source: "software_engineering_kapitel_07"
---

# [[Akteur Rollen]]

- **Kernkonzept:** Akteur-Rollen definieren externe Entitäten (Nutzer, Fremdsysteme oder andere Systeme), die mit einem System interagieren, ohne Teil des Systems selbst zu sein. Sie repräsentieren die verschiedenen Perspektiven und Verantwortlichkeiten, aus denen heraus Anforderungen an das System gestellt werden.
- **Nutzen & Zweck:** Akteur-Rollen ermöglichen eine klare Trennung zwischen System und Umgebung, indem sie die beteiligten Stakeholder und ihre Interaktionen mit dem System strukturiert erfassen. Dies löst das Problem, Anforderungen ungeordnet oder aus unklaren Perspektiven zu sammeln, und schafft eine Grundlage für die Identifikation von Use Cases, die Priorisierung von Entwicklungsaufgaben sowie die Zuordnung von Verantwortlichkeiten im Entwicklungsprozess.
- **Abgrenzung & Grenzen:** Akteur-Rollen sollten nicht genutzt werden, um interne Systemkomponenten oder technische Schnittstellen zu modellieren, die keine eigenständigen externen Entitäten darstellen. Sie unterscheiden sich von Systemkomponenten, da sie keine Implementierungsdetails beschreiben, sondern ausschließlich die externe Sicht auf das System abbilden. Alternativen wie Datenflussdiagramme oder reine Anforderungslisten erfassen zwar ähnliche Informationen, bieten jedoch keine vergleichbare Strukturierung der Interaktionen zwischen Akteuren und System.
- **Beispiel / Code:** ```java
// Beispiel für ein UML-Use-Case-Diagramm (textuelle Notation)
@startuml
left to right direction
actor "Vereinsmanager" as manager
actor "Mail Client" as mail
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
}
manager --> UC1
mail --> UC1
UC1 --> UC2
UC1 --> UC3
@enduml
```

*Erläuterung:* Der `Vereinsmanager` und der `Mail Client` sind Akteure, die mit dem Use Case `Mitglieder verwalten` interagieren. Die Akteure sind nicht Teil des Systems `MyClub`, sondern definieren die Rollen, aus denen Anforderungen an das System gestellt werden.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e2
- **Vorgänger / Parent:** [[Use_Case_Akteure]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Akteur]]
  - [[Use_Case]]
