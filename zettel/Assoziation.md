---
id: f3f33b0f-6b1b-42f7-bf1e-6582ff6cb869
title: "Assoziation"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - beziehung
  - modellierung
  - beziehungen
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Assoziation]]

- **Kernkonzept:** Eine [[Assoziation]] ist eine [[Beziehung|Beziehung]] zwischen [[Klasse|Klassen]], die eine [[Relation]] zwischen deren [[Instanz|Instanzen]] beschreibt. Sie kann gerichtet, benannt und mit [[Multiplizität]] versehen sein und modelliert [[Interaktion|Interaktionen]], ohne eine [[Besitz|Besitz]]- oder [[Lebensdauer]]-Abhängigkeit zu implizieren.
- **Nutzen & Zweck:** Sie ermöglicht die [[Modellierung]] von [[Zusammenhang|Zusammenhängen]] zwischen [[Entität|Entitäten]], wie [[Besitz]], [[Nutzung]] oder [[Kommunikation]], und ist grundlegend für die [[Domänenmodellierung]] und [[Datenmodellierung]]. [[Assoziation|Assoziationen]] bieten [[Flexibilität]] in der [[Modellierung]], da sie schwächere [[Beziehung|Beziehungen]] als [[Aggregation]] oder [[Komposition]] abbilden und keine [[Lebensdauer]]-Abhängigkeit voraussetzen. Sie sind besonders nützlich, um [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] zu fördern.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn eine stärkere [[Beziehung]] wie [[Aggregation]] oder [[Komposition]] benötigt wird, da diese eine [[Lebensdauer]]- oder [[Besitz|Besitz]]-Abhängigkeit zwischen [[Objekt|Objekten]] voraussetzen. [[Assoziation|Assoziationen]] sind weniger streng als [[Vererbung]] oder die [[Implementierung]] von [[Schnittstelle|Schnittstellen]] und können zu [[Unklare_Verantwortlichkeiten|unklaren Verantwortlichkeiten]] führen, wenn die [[Relation|Relationen]] nicht klar definiert oder dokumentiert sind. Sie sollten vermieden werden, wenn eine [[Kohäsion|hohe Kohäsion]] innerhalb einer [[Komponente]] angestrebt wird.
- **Beispiel / Code:** ```java
// Beispiel für [[Assoziation]] mit gerichteter Beziehung und [[Multiplizität]]
class Student {
    private String name;
    
    Student(String name) {
        this.name = name;
    }
}

class Kurs {
    private List<Student> teilnehmer;  // [[Multiplizität]]: 0..*
    private Dozent dozent;            // Gerichtete [[Assoziation]] zu [[Dozent]]
    
    Kurs(List<Student> teilnehmer, Dozent dozent) {
        this.teilnehmer = teilnehmer;
        this.dozent = dozent;
    }
}

class Dozent {
    private String name;
    
    Dozent(String name) {
        this.name = name;
    }
}

// Bidirektionale [[Assoziation]] zwischen Verein und Mitglied
public class Verein {
    private List<Mitglied> mitglieder;
    
    public void hinzufuegenMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
        mitglied.setAktivBei(this);
    }
}

public class Mitglied {
    private Verein aktivBei;
    
    public void setAktivBei(Verein verein) {
        this.aktivBei = verein;
    }
}
```
