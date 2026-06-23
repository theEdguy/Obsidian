---
id: ee54d279-5852-4b13-9ab6-aab3fb9110c8
title: "Akteur Assoziation"
date: 2026-06-23
tags:
  - software_engineering
  - assoziation
  - akteure
  - draft
source: "software_engineering_kapitel_07"
---

# [[Akteur Assoziation]]

- **Kernkonzept:** Eine Akteur-Assoziation beschreibt die Teilnahme eines Akteurs an einem Use Case und definiert die Kommunikationsbeziehung zwischen einer Instanz des Akteurs und dem Use Case. Sie zeigt, welche Akteure mit welchen Anwendungsfällen interagieren.
- **Nutzen & Zweck:** Die Akteur-Assoziation existiert, um klar zu dokumentieren, welche externen Entitäten (Akteure) mit welchen Funktionen (Use Cases) eines Systems interagieren. Sie löst das Problem der unklaren Verantwortlichkeiten und Schnittstellen zwischen System und Umgebung, indem sie visuelle und strukturelle Übersicht schafft. Dadurch wird die Analyse von Anforderungen erleichtert und die Grundlage für die weitere Systemgestaltung gelegt.
- **Abgrenzung & Grenzen:** Eine Akteur-Assoziation sollte nicht genutzt werden, um zeitliche Abfolgen oder prozessuale Abläufe zwischen Use Cases darzustellen. Sie unterscheidet sich von Generalisierung oder Include/Extend-Beziehungen, da sie keine Vererbung oder funktionale Abhängigkeiten zwischen Use Cases modelliert, sondern ausschließlich die Beteiligung von Akteuren. Assoziationen dürfen nicht weggelassen werden, selbst wenn Include- oder Extend-Beziehungen bestehen, da sonst die Akteursbeteiligung unklar bleibt.
- **Beispiel / Code:** ```uml
@startuml
left to right direction
actor Vereinsmanager
actor MailClient
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
}

Vereinsmanager --> UC1
MailClient --> UC1
@enduml
```

In diesem UML-Beispiel ist der *Vereinsmanager* über eine Assoziation mit dem Use Case *Mitglieder verwalten* verbunden, was zeigt, dass er direkt mit diesem Anwendungsfall interagiert. Der *MailClient* ist ebenfalls assoziiert, da er für die Benachrichtigungsfunktion benötigt wird.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b2b
- **Vorgänger / Parent:** [[Use_Case_Akteure]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Akteur]]
  - [[Use_Case]]
