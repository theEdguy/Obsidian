---
id: 0dbaf6d0-eeac-48be-9c9c-f556c1724913
title: "Spezialisierung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Spezialisierung]]

- **Kernkonzept:** Die [[Spezialisierung]] ist eine Form der [[Vererbung]], bei der [[Unterklasse|Unterklassen]] spezifischere [[Eigenschaft|Eigenschaften]] oder [[Verhalten]] als ihre [[Oberklasse]] definieren und das [[Ist-ein-Prinzip|'Ist-ein'-Prinzip]] realisieren. [[Instanz|Instanzen]] der [[Unterklasse]] bilden eine Teilmenge der [[Instanz|Instanzen]] der [[Oberklasse]] und erweitern oder überschreiben deren [[Schnittstelle|Schnittstellen]] und Implementierungen.
- **Nutzen & Zweck:** Die [[Spezialisierung]] ermöglicht die Wiederverwendung von [[Code]] und [[Struktur]] durch [[Vererbung]], reduziert [[Redundanz|Redundanzen]] und fördert eine klare, hierarchische Organisation von [[Klasse|Klassen]]. Sie löst das Problem der Modellierung von Gemeinsamkeiten und Unterschieden zwischen verwandten [[Entität|Entitäten]], indem sie eine logische [[Abstraktionsebene]] schafft, die sowohl [[Generalisierung]] als auch differenzierte Anpassungen erlaubt. Dadurch verbessert sie die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Modularität]] von [[Software-System|Software-Systemen]]. Zudem unterstützt sie die Umsetzung von [[Entwurfsmuster|Mustern]] wie [[Template_Method_Pattern]] oder [[Strategy_Pattern]].
- **Abgrenzung & Grenzen:** Die [[Spezialisierung]] sollte nicht genutzt werden, wenn keine echte [[Ist-ein-Prinzip|'Ist-ein'-Beziehung]] zwischen den [[Klasse|Klassen]] besteht, da dies zu semantischen Widersprüchen oder Verletzungen des [[Liskovschen_Substitutionsprinzip|Liskovschen Substitutionsprinzips]] führen kann (z. B. [[Quadrat]] als [[Unterklasse]] von [[Rechteck]], wenn das [[Verhalten]] nicht konsistent bleibt). Alternativen wie [[Komposition]] oder [[Schnittstelle|Schnittstellen]] sind vorzuziehen, wenn [[Lose_Kopplung]] oder Flexibilität wichtiger sind als strikte [[Vererbung]]. Zudem sollte [[Mehrfachvererbung]] vermieden werden, wenn die [[Klassenhierarchie]] unklar oder überlappend ist (z. B. bei [[Disjoint_Beziehung|'disjoint'-Beziehungen]]). Übermäßige [[Spezialisierung]] kann zu unnötiger [[Komplexität]] oder [[Code_Duplication|Code-Duplikation]] führen und die [[Kohäsion]] verringern. Bei tiefen [[Vererbungshierarchie|Vererbungshierarchien]] sollte geprüft werden, ob [[Refactoring]] oder der Einsatz von [[Delegation]] sinnvoller ist.
- **Beispiel / Code:** ```java
// Oberklasse
public class Team {
    protected String name;
    
    public Team(String name) {
        this.name = name;
    }
    
    public int leistungsprognose(Date datum) {
        return 0; // Standardimplementierung
    }
}

// Unterklasse (Spezialisierung)
public class FitaTeam extends Team {
    public FitaTeam(String name) {
        super(name);
    }
    
    @Override
    public int leistungsprognose(Date datum) {
        return 50; // Spezifische Implementierung
    }
}

// Beispiel aus der UML-Modellierung
class Fahrzeug {
    protected String marke;
    
    public Fahrzeug(String marke) {
        this.marke = marke;
    }
    
    public void fahren() {
        System.out.println("Das Fahrzeug bewegt sich.");
    }
}

// Unterklasse (Spezialisierung)
class Auto extends Fahrzeug {
    private int anzahlTueren;
    
    public Auto(String marke, int anzahlTueren) {
        super(marke);
        this.anzahlTueren = anzahlTueren;
    }
    
    @Override
    public void fahren() {
        System.out.println("Das Auto fährt auf der Straße.");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[Vererbungssemantik]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
