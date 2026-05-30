---
id: 5867f2b8-d736-4fbc-93d7-c12b721596d3
title: "Verantwortlichkeiten_zuweisen"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Verantwortlichkeiten_zuweisen]]

- **Kernkonzept:** [[Verantwortlichkeiten_zuweisen]] ist ein zentrales [[Designprinzip]] im [[Objektorientierte_Programmierung|objektorientierten Design]], bei dem definiert wird, welche [[Klasse]] für welche [[Aufgabe|Aufgaben]] (z. B. Wissen oder Handeln) zuständig ist.
- **Nutzen & Zweck:** Es fördert die [[Kohäsion]] und [[Lose_Kopplung|lose Kopplung]] von [[Klasse|Klassen]], indem [[Verantwortlichkeit|Verantwortlichkeiten]] klar verteilt und [[Komplexität]] reduziert wird.
- **Abgrenzung & Grenzen:** Nicht anwendbar, wenn [[Klasse|Klassen]] zu viele [[Verantwortlichkeit|Verantwortlichkeiten]] übernehmen (Verstoß gegen [[Single_Responsibility_Principle]]). Unterscheidet sich von prozeduralem Design, bei dem [[Funktionalität|Funktionalitäten]] nicht klar zugeordnet sind.
- **Beispiel / Code:** ```java
// Beispiel für Delegation
class ManagementFacade {
    private ManageMembers manager;

    public void manageMembers(Token token) {
        this.manager.manageMembers(token); // Verantwortung wird delegiert
    }
}
```
