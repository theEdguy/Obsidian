---
id: 10371d14-7fd8-40f8-a510-10963421fefe
title: "Typischer_Fehler_Attribut_statt_Konzept"
date: 2026-05-30
tags:
  - software_engineering
  - analyse
  - objektorientierung
  - domänenmodellierung
  - draft
source: "SWE Slides (Folien 181-195)"
---

# [[Typischer_Fehler_Attribut_statt_Konzept]]

- **Kernkonzept:** Der [[Typischer_Fehler_Attribut_statt_Konzept|typische Fehler]], ein [[Konzept]] der [[Problemdomäne]] fälschlich als [[Attribut]] eines anderen [[Objekt|Objekts]] zu modellieren, führt zu einer unangemessenen [[Vereinfachung]] der [[Domänenlogik]]. [[Konzept|Konzepte]] sollten als eigenständige [[Entität|Entitäten]] modelliert werden.
- **Nutzen & Zweck:** Die korrekte Identifikation von [[Konzept|Konzepten]] als [[Entität|Entitäten]] statt [[Attribut|Attribute]] verhindert [[Designfehler|Designfehler]] wie [[Starke_Kopplung|starke Kopplung]] oder [[Verlust_von_Domänenwissen|Verlust von Domänenwissen]]. Sie fördert eine [[Erweiterbare_Architektur|erweiterbare Architektur]] und [[Wartbarkeit]].
- **Abgrenzung & Grenzen:** Nicht jedes [[Attribut]] ist ein [[Konzept]]. [[Quantität|Quantitäten]], [[Text|Texte]] oder [[Adjektiv|Adjektive]] (z. B. Farben) sollten als [[Attribut|Attribute]] modelliert werden. Die Faustregel lautet: [[Konzept|Konzepte]], die man "anfassen" kann, sind keine [[Attribut|Attribute]].
- **Beispiel / Code:** ```uml
@startuml
"Falsch:" class Verein {
  -mitglieder: Mitglied[1..*]
}

"Richtig:" class Verein
class Mitglied {
  -status: Status
}
Verein "1" -- "*" Mitglied: hat >
@enduml
```
