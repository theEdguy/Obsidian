---
id: a4c9683e-aa18-4d38-bdf3-d0f37a16cd1e
title: "Pin_(UML)"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - datenfluss
  - modellierung
  - draft
source: "SWE Slides (Folien 181-195)"
---

# [[Pin_(UML)]]

- **Kernkonzept:** Ein [[Pin_(UML)|Pin]] ist ein [[Modellelement]] in [[Activity-Diagramm|Activity-Diagrammen]], das den [[Datenfluss]] zwischen [[Aktivität|Aktivitäten]] durch [[Eingabe|Eingaben]] und [[Ausgabe|Ausgaben]] explizit modelliert. [[Pin_(UML)|Pins]] repräsentieren [[Parameter]] von [[Aktivität|Aktivitäten]] und ermöglichen die [[Typisierung]] von [[Daten]].
- **Nutzen & Zweck:** [[Pin_(UML)|Pins]] ermöglichen die präzise Modellierung von [[Datenfluss|Datenflüssen]] in [[Prozess|Prozessen]] und unterstützen die [[Validierung]] von [[Daten|Datentypen]] und [[Wert|Werten]]. Sie sind essenziell für die [[Schnittstellenbeschreibung]] zwischen [[Aktivität|Aktivitäten]] in komplexen [[System|Systemen]].
- **Abgrenzung & Grenzen:** Nicht zu verwechseln mit [[Parameter|Parametern]] in [[Programmiersprache|Programmiersprachen]], die [[Code]]-Ebene betreffen. [[Pin_(UML)|Pins]] sind rein konzeptionell und dienen der [[Modellierung]] auf [[Design]]-Ebene. Sie sind nicht für die Darstellung von [[Kontrollfluss|Kontrollflüssen]] geeignet.
- **Beispiel / Code:** ```uml
@startuml
start
:Eis zerkleinern;
partition "Eingabe" {
  :Eis [gestoßen];
}
partition "Ausgabe" {
  :Eis [zerkleinert];
}
:Cocktail mixen;
stop
@enduml
```
