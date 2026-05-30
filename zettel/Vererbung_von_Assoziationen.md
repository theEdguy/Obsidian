---
id: c1893216-e6b6-4350-9155-385bd6b07b24
title: "Vererbung_von_Assoziationen"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Vererbung_von_Assoziationen]]

- **Kernkonzept:** [[Assoziation|Assoziationen]] werden in [[Vererbungshierarchie|Vererbungshierarchien]] an [[Unterklasse|Unterklassen]] vererbt, sodass [[Unterklasse|Unterklassen]] die [[Beziehung|Beziehungen]] ihrer [[Oberklasse|Oberklassen]] erben.
- **Nutzen & Zweck:** Sie ermöglicht die Wiederverwendung von [[Assoziation|Assoziationen]] in [[Vererbungshierarchie|Vererbungshierarchien]], um [[Redundanz]] zu vermeiden und die [[Konsistenz]] des [[Modell|Modells]] zu wahren.
- **Abgrenzung & Grenzen:** Kann zu unerwünschten [[Seiteneffekt|Seiteneffekten]] führen, wenn die [[Assoziation]] in [[Unterklasse|Unterklassen]] nicht sinnvoll ist. Sollte nur verwendet werden, wenn die [[Beziehung]] für alle [[Unterklasse|Unterklassen]] gilt.
- **Beispiel / Code:** ```java
class LigaTeam extends Team {
    // Erbt die Assoziation zu Mitglied von Team
}
```
