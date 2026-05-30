---
id: 0f009cf4-0780-439b-9cd0-9514961ca135
title: "Komposition"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - oop
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Komposition]]

- **Kernkonzept:** Die [[Komposition]] ist ein [[Designprinzip]] in der [[Objektorientierung|objektorientierten Programmierung]], das eine [[Teil-Ganzes-Beziehung]] beschreibt. Dabei werden [[Objekt|Objekte]] aus anderen [[Objekt|Objekten]] zusammengesetzt, um [[Funktionalität]] zu erweitern, ohne [[Vererbung]] zu nutzen. Die [[Teil|Teile]] sind existenzabhängig vom [[Ganzen]] und können nicht ohne dieses existieren, was eine starke [[Kopplung]] impliziert.
- **Nutzen & Zweck:** Die [[Komposition]] fördert [[Lose_Kopplung|lose Kopplung]] und [[Flexibilität]], da [[Komponente|Komponenten]] zur Laufzeit ausgetauscht werden können. Sie vermeidet Probleme der [[Vererbung]], wie [[Starke_Kopplung|starke Kopplung]], und ermöglicht die Modellierung von [[Hierarchie|hierarchischen Strukturen]], bei denen die [[Lebensdauer]] der [[Teil|Teile]] an die des [[Ganzen]] gebunden ist. Besonders nützlich ist sie bei der Strukturierung von [[GUI-Komponente|GUI-Komponenten]] oder [[Dokumentenstruktur|Dokumentenstrukturen]].
- **Abgrenzung & Grenzen:** Die [[Komposition]] erfordert mehr [[Boilerplate-Code]] als [[Vererbung]] und kann zu [[Komplexität]] führen, wenn zu viele [[Schichten]] entstehen. Sie ist nicht geeignet, wenn die [[Teil|Teile]] unabhängig vom [[Ganzen]] existieren können oder sollen – in solchen Fällen sollte eine [[Aggregation]] verwendet werden. Zudem ist sie weniger intuitiv für einfache [[Hierarchie|Hierarchien]].
- **Beispiel / Code:** ```java
// Beispiel für [[Komposition]] mit Existenzabhängigkeit der [[Teil|Teile]]
class Motor {
    void starten() {
        System.out.println("Motor startet");
    }
}

class Auto {
    private Motor motor;
    
    Auto() {
        this.motor = new Motor(); // Motor existiert nur mit dem Auto
    }
    
    void fahren() {
        motor.starten();
        System.out.println("Auto fährt");
    }
}

// Beispiel für [[Teil-Ganzes-Beziehung]] mit starker [[Kopplung]]
class Verein {
    private Vorstand vorstand;
    private List<Team> teams;
    
    Verein() {
        this.vorstand = new Vorstand(); // Vorstand existiert nur mit dem Verein
        this.teams = new ArrayList<>();
    }
}
```
