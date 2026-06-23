---
id: 559b3289-14c9-4ed2-b1ed-24e085017559
title: "Abstrakte_Klasse"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - entwurf
  - objektorientierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Abstrakte_Klasse]]

- **Kernkonzept:** Eine [[abstrakte_Klasse|abstrakte Klasse]] ist eine [[Klasse]], die keine direkten [[Instanz|Instanzen]] besitzt und bewusst unvollständig definiert ist, wobei mindestens eine [[Methode]] als [[abstrakte_Methode|abstrakt]] (ohne Implementierung) deklariert sein muss. Sie dient als [[Oberklasse]] für [[Unterklasse|Unterklassen]] und stellt gemeinsame [[Attribut|Attribute]] und [[Methode|Methoden]] bereit, die von [[Unterklasse|Unterklassen]] spezifisch implementiert werden müssen.
- **Nutzen & Zweck:** Eine [[abstrakte_Klasse]] ermöglicht die Definition gemeinsamer [[Schnittstelle|Schnittstellen]] und [[Verhalten]] für eine Gruppe verwandter [[Klasse|Klassen]], ohne eine konkrete Implementierung vorzugeben. Dies fördert die [[Wiederverwendbarkeit]] und [[Modularität]] im [[Softwareentwurf]] und löst das Problem der Redundanz, indem allgemeine Strukturen zentral definiert werden. Dadurch wird die [[Konsistenz]] im [[Design]] sichergestellt und die [[Erweiterbarkeit]] des Systems verbessert, da neue [[Unterklasse|Unterklassen]] einfach hinzugefügt werden können, ohne die bestehende [[Vererbung|Vererbungshierarchie]] zu stören. Zudem unterstützt sie die Umsetzung des [[Open-Closed_Principle|Open-Closed-Prinzips]] in der [[objektorientierten_Programmierung|objektorientierten Programmierung]].
- **Abgrenzung & Grenzen:** Eine [[abstrakte_Klasse]] sollte nicht genutzt werden, wenn keine gemeinsame Basislogik für mehrere [[Klasse|Klassen]] existiert oder wenn die [[Klasse]] direkt instanziiert werden muss. Im Gegensatz zu [[Schnittstelle|Schnittstellen]], die ausschließlich [[Methodensignatur|Methodensignaturen]] definieren, können [[abstrakte_Klasse|abstrakte Klassen]] bereits implementierte [[Methode|Methoden]] und [[Attribut|Attribute]] enthalten. Sie sind daher weniger flexibel als [[Schnittstelle|Schnittstellen]], wenn es um [[Mehrfachvererbung]] geht, da eine [[Klasse]] nur von einer [[abstrakte_Klasse|abstrakten Klasse]] erben kann. Zudem sind [[abstrakte_Klasse|abstrakte Klassen]] ungeeignet, wenn die [[Vererbung|Vererbungshierarchie]] zu starr ist und keine klare „[[Ist-ein-Beziehung|Ist-ein]]“-Beziehung zwischen [[Oberklasse]] und [[Unterklasse]] besteht. Eine [[abstrakte_Klasse]] ohne [[Unterklasse|Unterklassen]] ist sinnlos und widerspricht ihrem Zweck.
- **Beispiel / Code:** ```java
// Abstrakte Klasse mit einer abstrakten Methode und einer konkreten Methode
public abstract class Team {
    protected String name;
    
    public Team(String name) {
        this.name = name;
    }
    
    // Abstrakte Methode (ohne Implementierung)
    public abstract int leistungsprognose(Date datum);
    
    // Konkrete Methode
    public void teamInfo() {
        System.out.println("Team: " + name);
    }
}

// Konkrete Unterklasse
public class DDDTeam extends Team {
    public DDDTeam(String name) {
        super(name);
    }
    
    @Override
    public int leistungsprognose(Date datum) {
        return 42; // Beispielimplementierung
    }
}

// Weiteres Beispiel: Abstrakte Klasse mit gemeinsamer Logik
abstract class Tier {
    private String name;
    
    public Tier(String name) {
        this.name = name;
    }
    
    // Abstrakte Methode
    public abstract void geraeuschMachen();
    
    // Konkrete Methode
    public void schlafen() {
        System.out.println(name + " schläft.");
    }
}

// Konkrete Unterklasse
class Hund extends Tier {
    public Hund(String name) {
        super(name);
    }
    
    @Override
    public void geraeuschMachen() {
        System.out.println("Wuff!");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Vererbung]]
  - [[Interface]]
