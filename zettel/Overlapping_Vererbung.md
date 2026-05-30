---
id: b5353780-a21b-49cb-ab1c-cd4e997936c5
title: "Overlapping_Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Overlapping_Vererbung]]

- **Kernkonzept:** [[Overlapping_Vererbung]] beschreibt eine [[Vererbungsbeziehung]], bei der [[Instanz|Instanzen]] einer [[Unterklasse]] gleichzeitig [[Instanz|Instanzen]] mehrerer anderer [[Unterklasse|Unterklassen]] sein können. Dies ermöglicht [[Mehrfachvererbung]].
- **Nutzen & Zweck:** Sie erlaubt die Modellierung von [[Klasse|Klassen]], die [[Eigenschaft|Eigenschaften]] und [[Verhalten]] mehrerer [[Oberklasse|Oberklassen]] kombinieren, z. B. in [[Domänenmodellierung|Domänenmodellen]] mit überlappenden Kategorien.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn [[Unterklasse|Unterklassen]] sich gegenseitig ausschließen sollen (siehe [[Disjoint_Vererbung]]). [[Overlapping_Vererbung]] kann zu [[Diamond_Problem|Mehrdeutigkeiten]] führen, wenn nicht sorgfältig designed.
- **Beispiel / Code:** ```java
public class HerrenLigaTeam extends HerrenTeam, LigaTeam {
    // Kombination aus HerrenTeam und LigaTeam
}
```
