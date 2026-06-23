---
id: bb421dc0-95ab-443b-ac9d-df3463a04869
title: "Use Case Name"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - benennung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Use Case Name]]

- **Kernkonzept:** Der 'Use Case Name' ist die prägnante, verbale Bezeichnung eines Use Cases, die den zentralen Ablauf oder die Hauptfunktion aus Sicht der Akteure beschreibt. Er folgt typischerweise dem Muster 'Verb + Objekt' (z. B. 'Mitglieder verwalten') und dient als eindeutiger Identifikator für den Anwendungsfall im System.
- **Nutzen & Zweck:** Der Use Case Name existiert, um eine klare und einheitliche Kommunikation über die Funktionalität eines Systems zu ermöglichen. Er löst das Problem der Mehrdeutigkeit und Unstrukturiertheit bei der Beschreibung von Anforderungen, indem er eine standardisierte, leicht verständliche Benennung schafft. Dies erleichtert die Zuordnung von Anforderungen zu Use Cases, die Priorisierung und die spätere Umsetzung im Entwicklungsprozess.
- **Abgrenzung & Grenzen:** Ein Use Case Name sollte nicht als einzelner Schritt oder atomare Aktion formuliert werden (z. B. 'Status ändern'), da dies den Kontext und den zusammenhängenden Ablauf ignoriert. Alternativen wie reine Funktionslisten oder User Stories bieten keine vergleichbare Strukturierung für komplexe Interaktionen. Zudem sollte der Name keine technischen Details oder Implementierungsaspekte enthalten, sondern sich auf die fachliche Ebene konzentrieren. Nicht geeignet ist der Use Case Name, wenn es um nicht-funktionale Anforderungen geht, die sich nicht als Ablauf beschreiben lassen (z. B. Performance-Anforderungen).
- **Beispiel / Code:** ```java
// Beispiel für einen Use Case Namen in einem Use-Case-Diagramm (UML-Notation)
@startuml
left to right direction
actor Vereinsmanager
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
}
Vereinsmanager --> UC1
UC1 .> UC2 : <<include>>
UC1 .> UC3 : <<include>>
@enduml
```

// Beispiel für die textuelle Beschreibung eines Use Case:
Name: Mitglieder verwalten
Akteure: Vereinsmanager, Mail Client
Systemgrenze: MyClub
Prio: 1 (hoch)
Beschreibung: Der Vereinsmanager führt Änderungen an Mitgliedsdaten durch, z. B. Anlegen, Bearbeiten oder Löschen von Mitgliedern.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** [[Use_Case_Struktur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
