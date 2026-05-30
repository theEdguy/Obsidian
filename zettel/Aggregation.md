---
id: 008366f6-3add-4a8f-8463-482f27824abc
title: "Aggregation"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - beziehung
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Aggregation]]

- **Kernkonzept:** Die [[Aggregation]] ist eine spezielle Form der [[Assoziation|Assoziationen]], die eine [[Teil-Ganzes-Beziehung]] modelliert. Dabei können die [[Teil|Teile]] unabhängig vom [[Ganzen]] existieren und stellen eine schwächere [[Kopplung]] als die [[Komposition]] dar ("hat-ein"-Beziehung).
- **Nutzen & Zweck:** Die [[Aggregation]] fördert die [[Wiederverwendbarkeit]] und [[Modularität]] von [[Komponente|Komponenten]], indem sie [[Zusammensetzung|Zusammensetzungen]] ermöglicht, bei denen die [[Teil|Teile]] auch ohne das [[Ganze]] existieren können. Sie eignet sich besonders für Szenarien wie [[Team|Teams]] und deren [[Mitglied|Mitglieder]], bei denen die [[Lebensdauer]] der [[Teil|Teile]] nicht an das [[Ganze]] gebunden ist.
- **Abgrenzung & Grenzen:** Die [[Aggregation]] unterscheidet sich von der [[Komposition]] durch die unabhängige [[Lebensdauer]] der [[Teil|Teile]]: Bei der [[Aggregation]] werden die [[Teil|Teile]] nicht zerstört, wenn das [[Ganze]] zerstört wird. Sie ist nicht geeignet, wenn die [[Teil|Teile]] existenzabhängig vom [[Ganzen]] sein müssen, da dies zu einer schwächeren [[Kohäsion]] führen kann. In solchen Fällen sollte stattdessen die [[Komposition]] verwendet werden.
- **Beispiel / Code:** ```java
// Beispiel für [[Aggregation]] in Java
class Professor {
    private String name;

    Professor(String name) {
        this.name = name;
    }
}

class Universität {
    private List<Professor> professoren;

    Universität(List<Professor> professoren) {
        this.professoren = professoren;
    }
    // Professoren existieren unabhängig von der Universität
}

// Weiteres Beispiel: [[Team]] und [[Mitglied|Mitglieder]]
class Mitglied {
    private String name;

    Mitglied(String name) {
        this.name = name;
    }
}

class Team {
    private List<Mitglied> mitglieder;

    Team(List<Mitglied> mitglieder) {
        this.mitglieder = mitglieder;
    }
    // Mitglieder existieren unabhängig vom Team
}
```
