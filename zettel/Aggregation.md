---
id: 44cd9b5c-b898-4a9b-9709-b9b1920fcf76
title: "Aggregation"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - beziehung
  - objektorientierung
  - modellierung
  - uml
  - klassendiagramm
  - draft
source: "software_engineering_kapitel_05"
---

# [[Aggregation]]

- **Kernkonzept:** Die [[Aggregation]] ist eine spezielle Form der [[Assoziation|Assoziationen]] in der [[objektorientierten_Programmierung|objektorientierten Modellierung]], die eine [[Teil-Ganzes-Beziehung]] zwischen [[Klasse|Klassen]] beschreibt, bei der die [[Teil|Teile]] unabhängig vom [[Ganzen]] existieren können und keine [[Existenzabhängigkeit]] aufweisen. Sie stellt eine schwächere [[Kopplung]] als die [[Komposition]] dar und wird oft als "hat-ein"-Beziehung charakterisiert.
- **Nutzen & Zweck:** Die [[Aggregation]] fördert die [[Wiederverwendbarkeit]] und [[Modularität]] von [[Komponente|Komponenten]], indem sie [[Zusammensetzung|Zusammensetzungen]] ermöglicht, bei denen die [[Teil|Teile]] auch ohne das [[Ganze]] existieren und wiederverwendet werden können. Sie eignet sich besonders für die Modellierung von hierarchischen [[Struktur|Strukturen]], wie [[Team|Teams]] und deren [[Mitglied|Mitglieder]], [[Abteilung|Abteilungen]] und [[Angestellte|Angestellten]] oder [[Bibliothek|Bibliotheken]] und [[Buch|Büchern]], bei denen die [[Lebensdauer]] der [[Teil|Teile]] nicht an das [[Ganze]] gebunden ist. Durch die [[lose_Kopplung|lose Kopplung]] zwischen [[Aggregat]] und [[Teil|Teilen]] wird die [[Flexibilität]] des [[Softwaresystem|Systems]] erhöht, was [[Refactoring]] und [[Erweiterbarkeit]] erleichtert.
- **Abgrenzung & Grenzen:** Die [[Aggregation]] unterscheidet sich von der [[Komposition]] durch die unabhängige [[Lebensdauer]] der [[Teil|Teile]]: Bei der [[Aggregation]] werden die [[Teil|Teile]] nicht zerstört, wenn das [[Ganze]] zerstört wird, während bei der [[Komposition]] die [[Existenzabhängigkeit]] der [[Teil|Teile]] vom [[Ganzen]] besteht. Sie ist daher nicht geeignet, wenn die [[Teil|Teile]] ohne das [[Ganze]] nicht sinnvoll existieren können, da dies zu einer schwächeren [[Kohäsion]] führen kann. Im Vergleich zur allgemeinen [[Assoziation]] drückt die [[Aggregation]] eine semantisch stärkere [[Teil-Ganzes-Beziehung]] aus, ohne jedoch eine strikte Kontrolle über die [[Lebensdauer]] der [[Teil|Teile]] zu erfordern. Bei der Modellierung sollte darauf geachtet werden, dass die [[Aggregation]] nicht fälschlicherweise für [[Existenzabhängigkeit|existenzabhängige]] [[Beziehung|Beziehungen]] verwendet wird, da dies zu unerwartetem [[Verhalten]] im [[System]] führen kann.
- **Beispiel / Code:** ```java
// Beispiel für [[Aggregation]] in Java: Universität und Professoren
class Professor {
    private String name;
    
    public Professor(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
}

class Universität {
    private List<Professor> professoren;
    
    public Universität() {
        this.professoren = new ArrayList<>();
    }
    
    public void hinzufuegenProfessor(Professor professor) {
        professoren.add(professor);
    }
    
    public List<Professor> getProfessoren() {
        return new ArrayList<>(professoren); // Rückgabe einer Kopie zur Wahrung der [[Kapselung]]
    }
}

// Nutzung:
Professor prof1 = new Professor("Dr. Müller");
Professor prof2 = new Professor("Dr. Schmidt");
Universität uni = new Universität();
uni.hinzufuegenProfessor(prof1);
uni.hinzufuegenProfessor(prof2);
// Die Professoren existieren unabhängig von der Universität und können auch in anderen Kontexten verwendet werden.

// Weiteres Beispiel: [[Team]] und [[Mitglied|Mitglieder]]
class Mitglied {
    private String name;
    
    public Mitglied(String name) {
        this.name = name;
    }
    
    public String getName() {
        return name;
    }
}

class Team {
    private List<Mitglied> mitglieder;
    
    public Team() {
        this.mitglieder = new ArrayList<>();
    }
    
    public void hinzufuegenMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
    
    public List<Mitglied> getMitglieder() {
        return new ArrayList<>(mitglieder);
    }
}

// Nutzung:
Mitglied mitglied1 = new Mitglied("Max");
Mitglied mitglied2 = new Mitglied("Anna");
Team team = new Team();
team.hinzufuegenMitglied(mitglied1);
team.hinzufuegenMitglied(mitglied2);
// Die Mitglieder existieren auch nach Löschung des Teams weiter und können anderen Teams zugeordnet werden.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a2
- **Vorgänger / Parent:** [[Klassendiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Klassendiagramm]]
  - [[Komposition]]
  - [[Assoziation]]
