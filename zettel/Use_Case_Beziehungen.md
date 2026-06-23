---
id: 37387451-231a-4277-836c-214d10aac8d4
title: "Use Case Beziehungen"
date: 2026-06-23
tags:
  - software_engineering
  - beziehungen
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_09"
---

# [[Use Case Beziehungen]]

- **Kernkonzept:** Use Case [[Beziehung|Beziehungen]] definieren die strukturellen und funktionalen [[Zusammenhang|Zusammenhänge]] zwischen verschiedenen [[Use_Case|Use Cases]] in der [[UML]]-Modellierung, um [[Ablauf|Abläufe]], [[Abhängigkeit|Abhängigkeiten]] und [[Variante|Varianten]] systematisch darzustellen. Sie dienen der Strukturierung und Klarheit von [[Systemanforderung|Systemanforderungen]] und [[Ablauf|Abläufen]], indem sie logische Verbindungen wie [[Include-Beziehung]], [[Extend-Beziehung]] und [[Generalisierung]] modellieren.
- **Nutzen & Zweck:** Use Case [[Beziehung|Beziehungen]] ermöglichen die Wiederverwendung von [[Ablauf|Abläufen]], die klare Strukturierung komplexer [[System|Systeme]] und die Modellierung von [[Variante|Varianten]] oder [[Spezialisierung|Spezialisierungen]]. Sie lösen das Problem redundanter Beschreibungen und verbessern die Übersichtlichkeit in großen [[Use_Case|Use-Case-Diagrammen]], indem sie [[Abhängigkeit|Abhängigkeiten]], Wiederverwendbarkeit und Erweiterungen systematisch abbilden. Dadurch wird die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] optimiert und die spätere [[Implementierung]] erleichtert. Zudem tragen sie zur [[Modularisierung]] und [[Kohäsion]] des Modells bei, indem sie [[Schnittstelle|Schnittstellen]] zwischen [[Use_Case|Use Cases]] klar definieren.
- **Abgrenzung & Grenzen:** Use Case [[Beziehung|Beziehungen]] sollten nicht verwendet werden, um zeitliche [[Ablauf|Abläufe]] oder [[Workflow|Workflows]] darzustellen, da sie keine Sequenzinformationen abbilden. Hierfür sind [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Sequenzdiagramm|Sequenzdiagramme]] besser geeignet. Zudem sollten [[Beziehung|Beziehungen]] nicht als [[Vererbung|Vererbungshierarchien]] missverstanden werden, da sie keine [[Akteur|Akteurs]]-Assoziationen vererben. Bei einfachen [[System|Systemen]] mit wenigen [[Use_Case|Use Cases]] kann der Einsatz überflüssig sein und die Modellierung unnötig verkomplizieren. Übermäßige Verwendung von [[Beziehung|Beziehungen]] kann zu schwer wartbaren Modellen führen, insbesondere wenn keine funktionale [[Abhängigkeit|Abhängigkeit]] besteht. Sie unterscheiden sich zudem von [[Akteur|Akteurs]]-[[Use_Case|Use-Case-Beziehungen]], die Interaktionen zwischen [[Akteur|Akteuren]] und [[System|System]] beschreiben.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Vereinsmanager
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Mitglied löschen" as UC4
  usecase "Authentifizierung durchführen" as UC5
  usecase "Passwort zurücksetzen" as UC6
}

Vereinsmanager --> UC1
UC1 <|-- UC2
UC1 <|-- UC3
UC1 <|-- UC4
UC3 .> "<<extend>>" UC4 : [Bedingung: Austritt]
UC2 --> UC5 : <<include>>
UC3 <.. UC6 : <<extend>> [Bedingung: Passwort vergessen]
@enduml

// Beispiel für eine <<include>>-Beziehung (textuell):
// Der [[Use_Case|Use Case]] "Mitglied anlegen" beinhaltet zwingend den [[Use_Case|Use Case]] "Authentifizierung durchführen".
// Beispiel für eine <<extend>>-Beziehung:
// Der [[Use_Case|Use Case]] "Mitgliedsdaten bearbeiten" kann optional um "Passwort zurücksetzen" erweitert werden.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a3
- **Vorgänger / Parent:** [[Use-Case-Diagramm]]
- **Folgezettel / Unterzettel:**
  - [[include]]
  - [[extend]]
  - [[Generalisierung]]
- **Querverweise:**
  - [[UML]]
  - [[Anforderungsmodellierung]]
