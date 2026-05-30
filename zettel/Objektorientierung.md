---
id: 4b14d066-1b81-4247-a544-6bdeb57c38dc
title: "Objektorientierung"
date: 2026-05-30
tags:
  - software_engineering
  - paradigma
  - oop
  - programmierparadigma
  - draft
source: "SWE Slides (Folien 46-60)"
---

# [[Objektorientierung]]

- **Kernkonzept:** [[Objektorientierung]] ist ein zentrales [[Programmierparadigma]] der [[Software-Entwicklung]], das [[Software]] als Sammlung von [[Objekt|Objekten]] modelliert. Diese [[Objekt|Objekte]] kapseln [[Zustand]] und [[Verhalten]] und basieren auf den Prinzipien [[Klasse|Klassen]], [[Vererbung]], [[Polymorphie]] und [[Kapselung]], um reale [[Entität|Entitäten]] und deren [[Interaktion|Interaktionen]] abzubilden.
- **Nutzen & Zweck:** [[Objektorientierung]] löst das Problem der [[Komplexität]] und [[Wartbarkeit]] großer [[Software-Systeme]] durch [[Modularität]], [[Wiederverwendbarkeit]] und [[Abstraktion]]. Sie fördert die [[Erweiterbarkeit]] von [[Code]], indem sie [[Entwurfsmuster|Muster]] wie [[Observer_Pattern]] oder [[Strategy_Pattern]] ermöglicht und die [[Lose_Kopplung|lose Kopplung]] von [[Komponente|Komponenten]] unterstützt. Zudem verbessert sie die [[Kohäsion]] innerhalb von [[Modul|Modulen]] und erleichtert das [[Refactoring]] durch klare [[Schnittstelle|Schnittstellen]].
- **Abgrenzung & Grenzen:** [[Objektorientierung]] ist nicht universell einsetzbar und stößt in [[Problembereich|Problembereichen]] mit hohen [[Performance]]-Anforderungen oder datenintensiven [[Algorithmus|Algorithmen]] an ihre Grenzen. In solchen Fällen können [[Funktionale_Programmierung|funktionale]] oder [[Prozedurale_Programmierung|prozedurale]] Ansätze besser geeignet sein, da sie weniger [[Overhead]] durch [[Objekt|Objekte]] und [[Klasse|Klassenhierarchien]] verursachen. Zudem erfordert [[Objektorientierung]] ein sorgfältiges [[Design]], um [[Anti-Pattern|Anti-Patterns]] wie [[Gott-Klasse]] oder übermäßige [[Vererbung]] zu vermeiden, die zu hoher [[Kopplung]] und geringer [[Kohäsion]] führen können.
- **Beispiel / Code:** ```java
// Beispiel für [[Klasse]], [[Vererbung]], [[Polymorphie]] und [[Kapselung]]
public class Tier {
    private String name;

    public Tier(String name) {
        this.name = name;
    }

    public void machenGeräusch() {
        System.out.println("Tier macht Geräusch");
    }
}

class Hund extends Tier {
    public Hund(String name) {
        super(name);
    }

    @Override
    public void machenGeräusch() {
        System.out.println("Wuff!");
    }
}

// Beispiel für [[Kapselung]] und [[Zustand]]
public class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```
