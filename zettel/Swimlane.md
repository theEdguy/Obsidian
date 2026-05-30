---
id: 8dc22cd9-3018-40eb-ab23-4b7fc32bf282
title: "Swimlane"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - prozessmodellierung
  - organisation
  - draft
source: "SWE Slides (Folien 181-195)"
---

# [[Swimlane]]

- **Kernkonzept:** Eine [[Swimlane]] ist ein Strukturierungselement in [[Activity-Diagramm|Activity-Diagrammen]], das [[Aktivität|Aktivitäten]] nach [[Verantwortlichkeit|Verantwortlichkeiten]] oder [[Organisationseinheit|Organisationseinheiten]] gruppiert. Sie trennt [[Prozess|Prozesse]] in logische Bereiche wie [[Akteur|Akteure]], [[System|Systeme]] oder Abteilungen.
- **Nutzen & Zweck:** [[Swimlane|Swimlanes]] verdeutlichen die [[Verteilung]] von [[Aufgabe|Aufgaben]] in [[Geschäftsprozess|Geschäftsprozessen]] oder [[Use-Case|Use-Cases]] und helfen, [[Schnittstelle|Schnittstellen]] zwischen [[Rolle|Rollen]] oder [[System|Systemen]] zu identifizieren. Sie fördern die [[Transparenz]] in [[Kollaborationsmodell|Kollaborationsmodellen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für die Modellierung von [[Datenfluss|Datenflüssen]] ohne [[Organisationsbezug]] oder für die Darstellung von [[Zustand|Zuständen]] einzelner [[Objekt|Objekte]]. Im Gegensatz zu [[Partition_(UML)|Partitionen]] in [[UML]] sind [[Swimlane|Swimlanes]] explizit auf [[Organisationseinheit|Organisationseinheiten]] ausgerichtet.
- **Beispiel / Code:** ```uml
@startuml
|MyClub|
start
:Nachricht an die Abteilungsleitung generieren;
|Mail Client|
:Mail versenden;
:Versand protokollieren;
stop
@enduml
```
