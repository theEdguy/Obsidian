---
id: 4e52031a-34fc-4636-bc77-dad19a9fdabb
title: "Dependency_Beziehung"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - design_principle
  - draft
source: "SWE Slides (Folien 121-135)"
---

# [[Dependency_Beziehung]]

- **Kernkonzept:** Eine [[Dependency_Beziehung|Dependency-Beziehung]] modelliert eine lose, dynamische Verbindung zwischen [[Klasse|Klassen]], bei der eine [[Klasse]] temporär auf eine andere zugreift, ohne eine dauerhafte [[Assoziation]] einzugehen. Sie wird im [[UML-Diagramm]] mit einem gestrichelten Pfeil (`<<use>>`) dargestellt.
- **Nutzen & Zweck:** Sie macht [[Abhängigkeit|Abhängigkeiten]] im [[Softwaredesign]] explizit sichtbar, ohne eine feste [[Kopplung]] zu erzwingen. Besonders nützlich bei [[Schnittstelle|Schnittstellen]] oder temporären [[Objekt|Objekt]]-Interaktionen, um [[Modularität]] zu erhöhen.
- **Abgrenzung & Grenzen:** Nicht geeignet für dauerhafte [[Beziehung|Beziehungen]] wie [[Aggregation]] oder [[Komposition]]. Übermäßige Nutzung kann auf [[Designproblem|Designprobleme]] wie [[Zyklische_Abhängigkeit|zyklische Abhängigkeiten]] hinweisen. Alternativen: [[Assoziation]], [[Vererbung]] oder [[Delegation]].
- **Beispiel / Code:** ```java
public int leistungsprognose(Date datum) {
    // Temporäre Nutzung von [[Wettkampf]] ohne feste [[Assoziation]]
    return team[i].wettkampf[k].maxPunkte();
}
```
