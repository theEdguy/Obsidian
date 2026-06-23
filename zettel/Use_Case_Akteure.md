---
id: e25841be-0ea2-4047-a1c9-5e08573f0379
title: "Use Case Akteure"
date: 2026-06-23
tags:
  - software_engineering
  - akteure
  - modellierung
  - uml
  - analyse
  - draft
source: "software_engineering_kapitel_08"
---

# [[Use Case Akteure]]

- **Kernkonzept:** Use Case [[Akteur|Akteure]] sind externe [[Entität|Entitäten]] (z. B. [[Benutzer|Benutzer]], [[System|Systeme]] oder Organisationen), die mit einem zu entwickelnden [[System]] interagieren, um ein bestimmtes Ziel zu erreichen. Sie stehen außerhalb der [[Systemgrenze]] und initiieren oder beteiligen sich an [[Use_Case|Use Cases]], um funktionale [[Anforderung|Anforderungen]] aus externer Perspektive zu erfassen und zu strukturieren.
- **Nutzen & Zweck:** Das Konzept der [[Akteur|Akteure]] dient dazu, die [[Schnittstelle|Schnittstellen]] eines [[System|Systems]] präzise zu identifizieren und zu dokumentieren, indem es aufzeigt, wer oder was mit dem [[System]] interagiert. Dies ermöglicht eine klare Abgrenzung der [[Systemverantwortlichkeit|Systemverantwortlichkeiten]] und bildet die Grundlage für die Modellierung von [[Use_Case|Use Cases]], um [[Anforderung|Anforderungen]] aus der Sicht externer [[Stakeholder]] zu erfassen, zu priorisieren und Missverständnisse zu reduzieren. [[Akteur|Akteure]] verbessern die Kommunikation zwischen [[Stakeholder|Stakeholdern]], unterstützen die [[Modularisierung]] des [[System|Systems]] durch Sichtbarmachung externer Abhängigkeiten und erhöhen die [[Kohäsion]] der [[Use_Case|Use Cases]]. Zudem fördern sie eine zielgerichtete Analyse und Modellierung, indem sie sicherstellen, dass alle relevanten externen [[Entität|Entitäten]] und deren Bedürfnisse berücksichtigt werden.
- **Abgrenzung & Grenzen:** [[Akteur|Akteure]] sollten nicht mit internen [[Systemkomponente|Systemkomponenten]], [[Rolle|Rollen]] innerhalb des [[System|Systems]] oder konkreten Personen verwechselt werden, da sie ausschließlich abstrakte, externe [[Entität|Entitäten]] repräsentieren. Sie eignen sich nicht zur Modellierung von zeitlichen Abläufen, technischen [[Implementierungsdetail|Details]], rein internen Prozessen oder [[Algorithmus|Algorithmen]], die keine Interaktion mit externen [[Entität|Entitäten]] erfordern. Für solche Fälle sind Alternativen wie [[Aktivitätsdiagramm|Aktivitätsdiagramme]], [[Sequenzdiagramm|Sequenzdiagramme]], [[Zustandsdiagramm|Zustandsdiagramme]] oder [[Datenflussdiagramm|Datenflussdiagramme]] besser geeignet. Ein [[Use_Case]] ohne [[Akteur|Akteure]] ist kein valider Use Case, da keine externe Interaktion stattfindet. Zudem sollten [[Akteur|Akteure]] nicht zur Darstellung von [[Implementierungsdetail|Implementierungsdetails]] oder internen Datenflüssen verwendet werden, um den Fokus auf die Nutzer- und [[Schnittstelle|Schnittstellen]]-Perspektive zu wahren.
- **Beispiel / Code:** ```java
// Beispiel für ein Use-Case-Diagramm in UML-Notation (textuell beschrieben)
@startuml
left to right direction
actor "Vereinsmanager" as Manager
actor "MailClient" as Mail
actor "Mitglied" as Mitglied
actor "Administrator" as Admin

rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Mitglied löschen" as UC4
  usecase "Mitglied anmelden" as UC5
}

Manager --> UC1
Manager --> UC2
Manager --> UC3
Manager --> UC4
Mitglied --> UC5
Mitglied --> UC3
Admin --> UC2
Admin --> UC3
Admin --> UC4
Mail --> UC1 : "Benachrichtigung senden"
@enduml
```

// Erläuterung der Akteure im Use Case "Mitglieder verwalten":
- **Vereinsmanager**: Initiiert die [[Verwaltung]] von [[Mitglied|Mitgliedern]] (z. B. Anlegen, Bearbeiten, Löschen) und repräsentiert einen menschlichen [[Stakeholder]].
- **MailClient**: Externes [[System]], das bei Änderungen (z. B. Abteilungswechsel) benachrichtigt wird. Es handelt sich um einen nicht-menschlichen [[Akteur]], der eine [[Schnittstelle]] zu einem [[Event-gesteuertes_System|Event-gesteuerten System]] darstellt.
- **Mitglied**: Interagiert mit dem [[System]], um sich anzumelden oder eigene Daten zu bearbeiten.
- **Administrator**: Verfügt über erweiterte Berechtigungen (z. B. Löschen von [[Mitglied|Mitgliedern]]) und ist eine spezifischere [[Rolle]] im Vergleich zum [[Vereinsmanager]].

// Ergänzendes Beispiel für Generalisierung von Akteuren:
@startuml
actor "Benutzer" as User
actor "Administrator" as Admin
actor "Gast" as Guest

User <|-- Admin
User <|-- Guest
@enduml
```

*Erläuterung:* Die [[Generalisierung]] von [[Akteur|Akteuren]] zeigt, wie ein allgemeiner [[Benutzer]] durch spezifischere [[Rolle|Rollen]] wie [[Administrator]] oder [[Gast]] erweitert wird. Dies ermöglicht die Wiederverwendung gemeinsamer [[Anforderung|Anforderungen]] und eine klare Hierarchisierung der [[Schnittstelle|Schnittstellen]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Use_Case]]
- **Folgezettel / Unterzettel:**
  - [[Akteur_Identifikation]]
  - [[Akteur_Rolle]]
- **Querverweise:**
  - [[Systemgrenze]]
  - [[Anwendungsfall]]
