---
id: 5ae774c6-20b5-4e48-8759-b913c5ac5dd1
title: "Disjoint_Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Disjoint_Vererbung]]

- **Kernkonzept:** [[Disjoint_Vererbung]] beschreibt eine [[Vererbungsbeziehung]], bei der [[Instanz|Instanzen]] einer [[Unterklasse]] nicht gleichzeitig [[Instanz|Instanzen]] einer anderen [[Unterklasse]] derselben [[Oberklasse]] sein können. [[Mehrfachvererbung]] ist hier sinnlos.
- **Nutzen & Zweck:** Sie erzwingt eine klare Trennung zwischen [[Unterklasse|Unterklassen]] und verhindert [[Mehrdeutigkeit]] in der [[Modellierung]]. Dies ist nützlich, wenn [[Klasse|Klassen]] sich gegenseitig ausschließen, z. B. bei [[Rolle|Rollen]] wie Junior/Senior.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn [[Instanz|Instanzen]] mehreren [[Unterklasse|Unterklassen]] angehören können (siehe [[Overlapping_Vererbung]]). [[Disjoint_Vererbung]] kann die [[Flexibilität]] der [[Modellierung]] einschränken.
- **Beispiel / Code:** ```java
// Disjoint: Ein Mitglied kann nicht gleichzeitig Junior und Senior sein
public class Junior extends Mitglied {}
public class Senior extends Mitglied {}
```
