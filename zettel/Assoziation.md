---
id: 89b4fff8-8b34-462f-a6c6-9d8a407fda54
title: "Assoziation"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - beziehung
  - modellierung
  - beziehungen
  - klassendiagramm
  - draft
source: "software_engineering_kapitel_05"
---

# [[Assoziation]]

- **Kernkonzept:** Eine [[Assoziation]] ist eine [[Beziehung|strukturelle Beziehung]] zwischen [[Klasse|Klassen]] in der [[Objektorientierte_Programmierung|objektorientierten Modellierung]], die beschreibt, wie [[Instanz|Instanzen]] dieser [[Klasse|Klassen]] miteinander in [[Relation|Verbindung]] stehen, [[Interaktion|interagieren]] oder [[Kommunikation|kommunizieren]] können. Sie stellt die allgemeinste Form der [[Beziehung|Beziehungen]] dar und kann [[Gerichtete_Assoziation|gerichtet]], benannt, mit [[Multiplizität|Multiplizitäten]] oder [[Attribut|Attributen]] versehen sein, ohne eine [[Besitz|Besitz]]- oder [[Lebensdauer]]-Abhängigkeit zu implizieren.
- **Nutzen & Zweck:** [[Assoziation|Assoziationen]] ermöglichen die [[Modellierung]] von realen [[Zusammenhang|Zusammenhängen]] zwischen [[Entität|Entitäten]] in einem [[Softwaresystem]], um deren [[Interaktion|Interaktionen]] und [[Zusammenarbeit]] abzubilden. Sie lösen das Problem, dass [[Objekt|Objekte]] ohne definierte [[Beziehung|Beziehungen]] nicht miteinander [[Kommunikation|kommunizieren]] oder [[Daten]] austauschen können, was für die [[Funktionalität]] eines Systems essenziell ist. Durch [[Assoziation|Assoziationen]] wird die [[Struktur]] eines Systems klarer und nachvollziehbarer, was die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Dokumentation]] verbessert. Sie fördern [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und sind grundlegend für die [[Domänenmodellierung]] und [[Datenmodellierung]]. Zudem bieten sie [[Flexibilität]] in der [[Modellierung]], da sie schwächere [[Beziehung|Beziehungen]] als [[Aggregation]] oder [[Komposition]] abbilden und keine [[Lebensdauer]]-Abhängigkeit voraussetzen.
- **Abgrenzung & Grenzen:** [[Assoziation|Assoziationen]] sollten nicht genutzt werden, wenn eine stärkere [[Beziehung]] wie [[Aggregation]], [[Komposition]] oder [[Vererbung]] benötigt wird, da diese eine [[Lebensdauer]]- oder [[Besitz|Besitz]]-Abhängigkeit zwischen [[Objekt|Objekten]] voraussetzen. Sie sind ebenfalls ungeeignet, wenn lediglich temporäre oder dynamische [[Beziehung|Beziehungen]] zwischen [[Objekt|Objekten]] bestehen, die keine strukturelle [[Relation]] erfordern – hier sind [[Abhängigkeit|Abhängigkeiten]] (Dependencies) die passendere Wahl. Zudem sollten [[Assoziation|Assoziationen]] vermieden werden, wenn die [[Beziehung]] zwischen [[Klasse|Klassen]] trivial ist oder keine semantische Bedeutung besitzt, da sie sonst zu [[Unklare_Verantwortlichkeiten|unklaren Verantwortlichkeiten]] oder [[Komplexität]] führen können. Bei der [[Modellierung]] ist darauf zu achten, dass [[Assoziation|Assoziationen]] nicht zu einer [[Geringe_Kohäsion|geringen Kohäsion]] innerhalb einer [[Komponente]] beitragen, da sie [[Lose_Kopplung|lose Kopplung]] begünstigen, was in manchen Fällen kontraproduktiv sein kann.
- **Beispiel / Code:** ```java
// Beispiel für [[Assoziation]] mit gerichteter Beziehung, [[Multiplizität]] und unidirektionaler/bidirektionaler Ausprägung

// Gerichtete [[Assoziation]] mit [[Multiplizität]] (0..*): Ein Kurs hat mehrere Teilnehmer (Studenten) und einen Dozenten
class Student {
    private String name;
    
    Student(String name) {
        this.name = name;
    }
}

class Dozent {
    private String name;
    
    Dozent(String name) {
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

// Bidirektionale [[Assoziation]] zwischen Verein und Mitglied mit wechselseitiger Referenz
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

// Unidirektionale [[Assoziation]]: Ein Mitglied übt mehrere Disziplinen aus, aber die Disziplin kennt ihre Mitglieder nicht
public class Mitglied {
    private List<Disziplin> disziplinen;
    
    public void hinzufuegenDisziplin(Disziplin disziplin) {
        disziplinen.add(disziplin);
    }
}

public class Disziplin {
    private String name;
    
    Disziplin(String name) {
        this.name = name;
    }
    // Keine Referenz auf Mitglied, da die [[Assoziation]] unidirektional ist
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1
- **Vorgänger / Parent:** [[Klassendiagramm]]
- **Folgezettel / Unterzettel:**
  - [[Binäre_Assoziation]]
  - [[Mehrstellige_Assoziation]]
  - [[Navigierbare_Assoziation]]
  - [[Assoziationsklasse]]
- **Querverweise:**
  - [[Klassendiagramm]]
  - [[Aggregation]]
  - [[Komposition]]
