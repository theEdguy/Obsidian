---
id: 91c2e636-d12c-4f1c-a80b-0b158c16f4da
title: "Disjoint_Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Disjoint_Vererbung]]

- **Kernkonzept:** [[Disjoint_Vererbung]] ist ein [[UML]]-Konzept, das eine [[Vererbungsbeziehung]] beschreibt, bei der [[Instanz|Instanzen]] einer [[Unterklasse]] nicht gleichzeitig [[Instanz|Instanzen]] anderer [[Unterklasse|Unterklassen]] derselben [[Oberklasse]] sein können. Es definiert eine strikte Trennung zwischen den [[Spezialisierung|Spezialisierungen]] einer [[Klasse]], sodass keine Überlappung der [[Instanz|Instanzenmengen]] existiert und [[Mehrfachvererbung]] sinnlos wird.
- **Nutzen & Zweck:** [[Disjoint_Vererbung]] erzwingt eine klare Trennung zwischen [[Unterklasse|Unterklassen]] und verhindert [[Mehrdeutigkeit]] in der [[Modellierung]]. Dies löst das Problem logischer Widersprüche, indem sichergestellt wird, dass eine [[Instanz]] nicht mehreren [[Unterklasse|Unterklassen]] gleichzeitig angehören darf. Besonders nützlich ist dies in Szenarien mit sich gegenseitig ausschließenden [[Kategorie|Kategorien]], wie z. B. bei der Unterscheidung zwischen [[Rolle|Junior- und Senior-Mitgliedern]] in einem Verein. Durch die strikte Trennung vereinfacht es die [[Modellierung]] und verbessert die [[Kohäsion]] der [[Klasse|Klassenhierarchie]].
- **Abgrenzung & Grenzen:** [[Disjoint_Vererbung]] sollte nicht genutzt werden, wenn [[Instanz|Instanzen]] einer [[Oberklasse]] gleichzeitig mehreren [[Unterklasse|Unterklassen]] angehören können, wie z. B. bei hybriden [[Rolle|Rollen]] (z. B. ein Teammitglied, das sowohl [[Spieler]] als auch [[Trainer]] ist). In solchen Fällen ist die Verwendung von [[Overlapping_Vererbung]] sinnvoller. Zudem ist [[Disjoint_Vererbung]] ungeeignet, wenn die [[Klassenhierarchie]] dynamisch erweitert werden soll, da sie eine starre Trennung der [[Unterklasse|Unterklassen]] erzwingt. Alternativen wie [[Komposition]] oder [[Schnittstelle|Interfaces]] können flexibler sein, wenn [[Vererbung]] zu restriktiv wirkt. Die Einschränkung der [[Flexibilität]] kann die [[Wartbarkeit]] des Systems beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel für Disjoint-Vererbung in Java
abstract class Mitglied {
    // Gemeinsame Attribute und Methoden für alle Mitglieder
    private String name;
    
    public Mitglied(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
}

// Disjoint-Vererbung: Ein Mitglied kann NICHT gleichzeitig JuniorMitglied UND SeniorMitglied sein
class JuniorMitglied extends Mitglied {
    public JuniorMitglied(String name) {
        super(name);
    }
    
    // Spezifische Methoden/Attribute für Junior-Mitglieder
    public void teilnahmeAnJuniorTraining() {
        System.out.println(getName() + " nimmt am Junior-Training teil.");
    }
}

class SeniorMitglied extends Mitglied {
    public SeniorMitglied(String name) {
        super(name);
    }
    
    // Spezifische Methoden/Attribute für Senior-Mitglieder
    public void teilnahmeAnSeniorTraining() {
        System.out.println(getName() + " nimmt am Senior-Training teil.");
    }
}
```

// UML-Notation für Disjoint-Vererbung:
// - Generalisierungspfeil mit {disjoint} markiert, um die strikte Trennung zu kennzeichnen.
// - Beispiel: Mitglied <|-- JuniorMitglied (disjoint) und Mitglied <|-- SeniorMitglied (disjoint).

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2
- **Vorgänger / Parent:** [[Vererbungssemantik]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
