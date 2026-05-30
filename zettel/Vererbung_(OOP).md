---
id: a3a47041-49a6-43b6-8f6d-5442b48a587f
title: "Vererbung_(OOP)"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - entwurfsmuster
  - modellierung
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Vererbung_(OOP)]]

- **Kernkonzept:** Ein [[Mechanismus|Mechanismus]] in der [[Objektorientierung|objektorientierten Programmierung]], bei dem eine [[Unterklasse|Unterklasse]] die [[Eigenschaft|Eigenschaften]] und [[Verhalten|Verhaltensweisen]] einer [[Oberklasse]] übernimmt, diese erweitern oder [[Überschreiben|überschreiben]] kann, jedoch nicht entfernen darf.
- **Nutzen & Zweck:** Fördert die [[Wiederverwendung|Wiederverwendung]] von [[Code]] und ermöglicht die Modellierung hierarchischer [[Beziehung|Beziehungen]] zwischen [[Entität|Entitäten]]. Unterstützt das [[Substitutionsprinzip]], sodass [[Instanz|Instanzen]] von [[Unterklasse|Unterklassen]] als [[Instanz|Instanzen]] ihrer [[Oberklasse]] behandelt werden können.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Ist-eine-Beziehung|„Ist-eine“-Beziehung]] verletzt wird (z. B. [[Quadrat]] und [[Rechteck]]). Führt zu [[Starke_Kopplung|starker Kopplung]] und kann die [[Kohäsion]] verringern. Alternativen wie [[Komposition]] oder [[Delegation]] sind oft vorzuziehen, um [[Flexibilität]] zu erhöhen.
- **Beispiel / Code:** ```java
// Oberklasse
class Mitglied {
    private String name;
    
    public Mitglied(String name) {
        this.name = name;
    }
    
    public void vorstellen() {
        System.out.println("Ich bin " + name + ", ein Mitglied.");
    }
}

// Unterklasse
class Spieler extends Mitglied {
    private int nummer;
    
    public Spieler(String name, int nummer) {
        super(name);
        this.nummer = nummer;
    }
    
    @Override
    public void vorstellen() {
        System.out.println("Ich bin " + super.name + ", Spieler Nr. " + nummer + ".");
    }
}
```
