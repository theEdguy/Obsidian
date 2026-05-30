---
id: 487daa5a-e664-4b4e-86bc-276fa52624cb
title: "Signal_in_Aktivitätsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - event_gesteuert
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Signal_in_Aktivitätsdiagramm]]

- **Kernkonzept:** [[Signal_in_Aktivitätsdiagramm|Signale]] in [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] ermöglichen die Modellierung von [[Ereignis|Ereignissen]], die von [[Aktion|Aktionen]] gesendet oder empfangen werden, um [[Asynchronität|asynchrone Abläufe]] darzustellen.
- **Nutzen & Zweck:** Sie helfen, [[Event-gesteuertes_System|Event-gesteuerte Abläufe]] oder [[Zeitgesteuerte_Aktion|zeitgesteuerte Aktionen]] in [[Workflows]] oder [[Algorithmus|Algorithmen]] zu modellieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung von [[Synchronisation|synchronen Abläufen]] oder [[Datenfluss|Datenflüssen]]. Hier sind [[Transition|Transitionen]] oder [[Objektknoten]] vorzuziehen.
- **Beispiel / Code:** ```plantuml
@startuml
:Timer starten;
(Timer) --> :Aktion auslösen : Signal
@enduml
```
Hier löst ein [[Timer]] eine [[Aktion]] aus, sobald das [[Signal]] empfangen wird.
