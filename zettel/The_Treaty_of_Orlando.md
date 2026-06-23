---
id: 9855575e-7f0f-4b66-ad80-fa9cfb4063e8
title: "The Treaty of Orlando"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - geschichte
  - draft
source: "software_engineering_kapitel_03"
---

# [[The Treaty of Orlando]]

- **Kernkonzept:** Das 'Treaty of Orlando' ist ein 1989 formuliertes Konzept, das die beiden fundamentalen Mechanismen der Vererbung in der objektorientierten Programmierung definiert: 'Empathy' (Nachempfinden) und 'Templates' (Vorlagenbasierte Objekterzeugung). Es erklärt, wie Objekte Verhalten und Eigenschaften anderer Objekte übernehmen oder auf Basis von Vorlagen neu erzeugt werden.
- **Nutzen & Zweck:** Das Konzept dient dazu, die theoretischen Grundlagen der Vererbung in der Objektorientierung zu klären und zu standardisieren. Es löst das Problem der uneinheitlichen Interpretation von Vererbungsmechanismen, indem es zwei zentrale Prinzipien benennt und formalisiert. Dadurch wird die Kommunikation über Vererbung präziser und die Implementierung in Programmiersprachen konsistenter gestaltet.
- **Abgrenzung & Grenzen:** Das 'Treaty of Orlando' sollte nicht als praktische Implementierungsanleitung verstanden werden, sondern als theoretisches Rahmenwerk. Es unterscheidet sich von konkreten Vererbungsmodellen in Programmiersprachen (z. B. Klassenvererbung in Java oder Prototypenvererbung in JavaScript) dadurch, dass es keine Syntax oder technische Umsetzung vorgibt. Für einfache Vererbungsfälle oder Sprachen ohne Mehrfachvererbung kann das Konzept zu abstrakt sein und bietet keinen direkten Nutzen. Zudem deckt es keine Aspekte wie Polymorphie oder Schnittstellen ab, die in modernen OO-Sprachen ebenfalls relevant sind.
- **Beispiel / Code:** ```java
// Beispiel für 'Empathy' (Nachempfinden): Ein Objekt nutzt Verhalten eines anderen Objekts,
// wenn es keine eigene Implementierung besitzt.
class Tier {
    void machenGeräusch() {
        System.out.println("Tier macht Geräusch");
    }
}

class Hund extends Tier {
    // Keine eigene Implementierung von machenGeräusch() – nutzt die des Elternobjekts (Empathy).
}

public class Main {
    public static void main(String[] args) {
        Hund hund = new Hund();
        hund.machenGeräusch(); // Ausgabe: "Tier macht Geräusch" (Nachempfinden des Verhaltens von Tier)
    }
}

// Beispiel für 'Templates': Ein neues Objekt wird auf Basis einer Vorlage (Klasse) erzeugt.
class Katze extends Tier {
    @Override
    void machenGeräusch() {
        System.out.println("Miau!"); // Eigenes Verhalten, basierend auf der Vorlage 'Tier'
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3c
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
