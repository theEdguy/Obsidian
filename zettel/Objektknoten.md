---
id: fd2c9260-3eb4-41e8-8e95-974971e56c17
title: "Objektknoten"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - datenfluss
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Objektknoten]]

- **Kernkonzept:** Ein [[Objektknoten]] in einem [[Aktivitätsdiagramm]] modelliert den [[Datenfluss]] zwischen [[Aktion|Aktionen]] und dient als Container für [[Objekt|Objekte]] eines definierten [[Typ|Typs]] mit begrenzter Kapazität.
- **Nutzen & Zweck:** Er ermöglicht die Darstellung des [[Datenfluss|Datenflusses]] in [[Ablauf|Abläufen]] und hilft, die [[Datenhaltung]] und [[Datenverarbeitung]] in [[Geschäftsprozess|Geschäftsprozessen]] oder [[Algorithmus|Algorithmen]] zu visualisieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Modellierung von [[Kontrollfluss|Kontrollflüssen]] oder [[Zustandsübergang|Zustandsübergängen]]. Hier sind [[Transition|Transitionen]] oder [[Zustandsdiagramm|Zustandsdiagramme]] vorzuziehen.
- **Beispiel / Code:** ```plantuml
@startuml
:Aktion 1;
(Objekt : Klasse) --> Aktion 2 : {weight = 1}
@enduml
```
Hier fließt ein [[Objekt]] der [[Klasse]] „Klasse“ von „Aktion 1“ zu „Aktion 2“.
