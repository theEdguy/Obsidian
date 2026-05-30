---
id: 36e9182f-96eb-4c82-87d8-dda442efb76c
title: "Analyse-Objektmodell"
date: 2026-05-30
tags:
  - software_engineering
  - analyse
  - objektorientierung
  - domänenmodellierung
  - draft
source: "SWE Slides (Folien 181-195)"
---

# [[Analyse-Objektmodell]]

- **Kernkonzept:** Das [[Analyse-Objektmodell]] ist ein [[Modell]] der [[Problemdomäne]], das [[Objekt|Objekte]], deren [[Attribut|Attribute]] und [[Beziehung|Beziehungen]] in der realen Welt abbildet. Es dient der [[Strukturierung]] des [[Problemraums]] vor der [[Implementierung]].
- **Nutzen & Zweck:** Das [[Analyse-Objektmodell]] hilft, die [[Komplexität]] der [[Problemdomäne]] zu reduzieren, indem es [[Kernkonzept|Kernkonzepte]] und deren [[Zusammenhang|Zusammenhänge]] identifiziert. Es bildet die Grundlage für das spätere [[Design]] und die [[Implementierung]] eines [[Systems]].
- **Abgrenzung & Grenzen:** Kein [[Klassendiagramm]] für die [[Implementierung]], da es keine [[Methode|Methoden]] oder [[Technische_Detail|technischen Details]] enthält. Es konzentriert sich auf die [[Problemdomäne]], nicht auf [[Lösungsraum|Lösungsaspekte]]. Im Gegensatz zum [[Datenmodell]] werden keine [[Datenbank|Datenbankstrukturen]] modelliert.
- **Beispiel / Code:** ```uml
@startuml
class Mitglied {
  -status: Status
}
class Abteilung {
  -name: String
}
Mitglied "1" -- "*" Abteilung: gehört zu >
@enduml
```
