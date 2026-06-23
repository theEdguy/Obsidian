---
id: 3dd90c0a-c1ca-43a7-80c2-135ff8406400
title: "Klassifikation"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Klassifikation]]

- **Kernkonzept:** [[Klassifikation]] ist die systematische Zusammenfassung gleichartiger [[Objekt|Objekte]] zu einer [[Klasse]], die deren gemeinsame [[Attribut|Attribute]], [[Operation|Operationen]] und [[Zusicherung|Zusicherungen]] beschreibt. [[Objekt|Objekte]] werden dabei als [[Instanz|Instanzen]] dieser [[Klasse]] betrachtet und ermöglichen eine strukturierte [[Modellierung]] komplexer [[Systeme]] durch [[Abstraktion]] und hierarchische [[Ordnung]].
- **Nutzen & Zweck:** [[Klassifikation]] löst das Problem der [[Wiederholung]] von [[Code]] und [[Struktur]] durch [[Wiederverwendbarkeit]] und [[Abstraktion]]. Sie reduziert die [[Komplexität]] von [[Systemen]], indem sie ähnliche [[Objekt|Objekte]] der realen Welt unter einem gemeinsamen Konzept bündelt. Dadurch fördert sie die [[Kohäsion]] und schafft eine einheitliche [[Schnittstelle|Sprache]] für [[Entwickler]], [[Anwender]] und [[Fachexperte|Fachexperten]]. Zudem bildet sie die Grundlage für [[Vererbung]] und [[Polymorphie]] in der [[Objektorientierung]] und ermöglicht die Anwendung von [[Entwurfsmuster|Entwurfsmustern]] wie [[Template_Method_Pattern]] oder [[Strategy_Pattern]].
- **Abgrenzung & Grenzen:** [[Klassifikation]] ist nicht sinnvoll, wenn [[Objekt|Objekte]] stark individuelle [[Eigenschaft|Eigenschaften]] aufweisen, die sich nicht sinnvoll generalisieren lassen, oder wenn die [[Modellierung]] zu einer unnötigen [[Abstraktion]] führt, die die [[Problemdomäne]] verkompliziert. In solchen Fällen können [[Funktionale_Programmierung|funktionale Ansätze]] oder [[Datengetriebene_Anwendungen|datenorientierte Ansätze]] geeigneter sein. Zudem ist [[Klassifikation]] weniger hilfreich, wenn die Beziehungen zwischen [[Objekt|Objekten]] dynamischer oder flüchtiger Natur sind, als dass sie sich in starren [[Klassenstruktur|Klassenstrukturen]] abbilden ließen. Bei [[Einzelobjekt|Einzelobjekten]] mit einzigartigen [[Eigenschaft|Eigenschaften]] oder in [[Datenstruktur|flachen Datenstrukturen]] kann [[Klassifikation]] sogar kontraproduktiv sein. Alternativ können [[Komposition]] oder [[Delegation]] eingesetzt werden, um Flexibilität zu wahren.
- **Beispiel / Code:** ```java
// Klassifikation: Gemeinsame Struktur und Verhalten für Mitglieder
abstract class Person {
    protected String name;
    protected String adresse;
    protected int alter;

    public Person(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
    }

    // Abstrakte Methode zur Vorstellung (wird in Subklassen implementiert)
    public abstract void vorstellen();

    // Gemeinsame Methode für alle Personen
    public void kontaktieren() {
        System.out.println("Kontakt: " + this.adresse);
    }
}

class Mitglied extends Person {
    private int leistung;

    public Mitglied(String name, String adresse, int alter, int leistung) {
        super(name, adresse, alter);
        this.leistung = leistung;
    }

    @Override
    public void vorstellen() {
        System.out.println("Ich bin " + name + ", " + alter + " Jahre alt, Leistung: " + leistung);
    }

    // Spezifische Methode für Mitglieder
    public int leistungsprognose() {
        return this.leistung * 2; // Beispielhafte Berechnung
    }
}

// Instanziierung von Objekten der Klasse Mitglied
Mitglied mitglied1 = new Mitglied("Anna", "Musterstraße 1", 28, 150);
Mitglied mitglied2 = new Mitglied("Paul", "Beispielweg 2", 35, 180);

mitglied1.vorstellen(); // Ausgabe: Ich bin Anna, 28 Jahre alt, Leistung: 150
mitglied2.leistungsprognose(); // Ausgabe: 360
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c
- **Vorgänger / Parent:** [[Klassen]]
- **Folgezettel / Unterzettel:**
  - [[Taxonomie]]
- **Querverweise:** keine
