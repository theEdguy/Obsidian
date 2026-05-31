---
aliases:
- Use_Case_Diagramm
date: 2026-05-30
id: 6ffa9970-2e9e-4250-81fe-e9a9e0fc1fd0
source: SWE Slides (Folien 151-165)
tags:
- software_engineering
- uml
- modellierung
- analyse
- draft
title: Use-Case-Diagramm
---

# [[Use-Case-Diagramm]]

- **Kernkonzept:** Ein [[Use-Case-Diagramm]] ist eine grafische [[Darstellung]] der [[Use_Case|Use-Cases]] eines [[Softwaresystem|Systems]], ihrer [[Akteur|Akteure]] und der [[Beziehung|Beziehungen]] zwischen ihnen (z. B. <<include>>, <<extend>>). Es gehört zur [[UML]].
- **Nutzen & Zweck:** Es schafft eine [[Übersicht]] über die [[Funktionalität]] des Systems und die [[Interaktion]] mit [[Akteur|Akteuren]], was die [[Kommunikation]] mit [[Stakeholder]]n und die [[Priorisierung]] von [[Entwicklungsaufgabe|Entwicklungsaufgaben]] erleichtert.
- **Abgrenzung & Grenzen:** Es ist kein [[Ablaufdiagramm]] – es zeigt *was* das System leistet, nicht *wie*. Im Gegensatz zu [[Klassendiagramm|Klassendiagrammen]] oder [[Sequenzdiagramm|Sequenzdiagrammen]] beschreibt es keine [[technische_Implementierung|technischen Implementierungen]].
- **Beispiel / Code:** 
- ```plaintext
@startuml
left to right direction
actor [[Vereinsmanager]]
rectangle MyClub {
  ([[Mitglieder_verwalten]]) as MV
  ([[Mitglied_anlegen]]) as MA
  MV --> MA : <<include>>
}
[[Vereinsmanager]] --> MV
@enduml
```
