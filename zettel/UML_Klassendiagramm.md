---
id: 4b3b9b2b-9448-4d71-ae5f-3ed3e445b170
title: "UML_Klassendiagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - softwarearchitektur
  - klassendiagramm
  - klassendiagramme
  - diagramm
  - klasse
  - struktur
  - draft
source: "software_engineering_kapitel_13"
---

# [[UML_Klassendiagramm]]

- **Kernkonzept:** Ein [[Diagrammtyp]] der [[UML]], der die [[Struktur]] eines [[System|Systems]] durch [[Klasse|Klassen]], deren [[Attribut|Attribute]], [[Operation|Operationen]] und [[Beziehung|Beziehungen]] (z. B. [[Vererbung_(OOP)|Vererbung]], [[Assoziation]], [[Aggregation]], [[Komposition]], [[Schnittstelle|Schnittstellen]] und [[Assoziationsklasse]]) grafisch darstellt. Es dient als abstrakte [[Blaupause]] für die [[Implementierung]] von [[Softwarekomponente|Softwarekomponenten]] in [[objektorientierte_Programmierung|objektorientierten Systemen]] und visualisiert die statische [[Architektur]] der [[Problemdomäne]] oder [[Softwarelösung]] auf konzeptioneller Ebene, unabhängig von dynamischen [[Ablauf|Abläufen]] oder zeitlichen [[Abhängigkeit|Abhängigkeiten]].
- **Nutzen & Zweck:** Das [[UML_Klassendiagramm]] löst das Problem unklarer [[Systemarchitektur|Systemarchitekturen]] und unübersichtlicher [[Dokumentation]], indem es eine standardisierte, visuelle [[Sprache]] zur Verfügung stellt, um komplexe [[Zusammenhang|Zusammenhänge]] zwischen [[Klasse|Klassen]], deren [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Wechselwirkung|Wechselwirkungen]] frühzeitig im [[Entwicklungsprozess]] zu dokumentieren und zu kommunizieren. Es ermöglicht [[Entwickler|Entwicklern]], [[Designentscheidung|Designentscheidungen]] zu validieren, [[Redundanz|Redundanzen]] zu erkennen und die [[Wartbarkeit]] von [[Software]] durch klare [[Strukturvorgabe|Strukturvorgaben]] zu erhöhen. Zudem dient es als [[Brücke]] zwischen [[Analyse]], [[Design]] und [[Implementierung]], indem es eine konsistente Grundlage für die [[Codegenerierung]] und [[Systemdokumentation]] schafft. Durch die Visualisierung von [[Abhängigkeit|Abhängigkeiten]] und [[Beziehung|Beziehungen]] unterstützt es die Identifikation von [[Kohäsion]] und [[Lose_Kopplung|lose gekoppelten]] [[Komponente|Komponenten]], was die [[Skalierbarkeit]] und [[Erweiterbarkeit]] des [[System|Systems]] verbessert. Klassendiagramme machen die Komplexität von Softwaresystemen beherrschbar, fördern die [[Wiederverwendbarkeit]] von [[Code]] und erleichtern die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] sowie die [[Einarbeitung]] neuer Teammitglieder. Sie schaffen eine einheitliche [[Sprache]] für [[Architektur]] und [[Design]], reduzieren [[Missverständnis|Missverständnisse]] im [[Entwicklungsprozess]] und unterstützen die [[Validierung]] von [[Anforderung|Anforderungen]] gegen die [[Systemarchitektur]]. Darüber hinaus fördern sie die explizite Darstellung von [[Vererbung_(OOP)|Vererbungs-]] und [[Assoziationsbeziehung|Assoziationsbeziehungen]], was die [[Wiederverwendbarkeit]] und [[Modularität]] des [[System|Systems]] erhöht. Klassendiagramme existieren, um die [[Architektur]] eines [[System|Systems]] frühzeitig und präzise zu planen, bevor mit der [[Implementierung]] begonnen wird, und bilden die Grundlage für die Generierung von [[Quellcode]] und die [[Dokumentation]].
- **Abgrenzung & Grenzen:** Ein [[UML_Klassendiagramm]] sollte nicht genutzt werden, wenn dynamische [[Ablauf|Abläufe]], zeitliche [[Abhängigkeit|Abhängigkeiten]] oder [[Verhalten]] von [[Objekt|Objekten]] im Vordergrund stehen – hierfür eignen sich [[UML_Sequenzdiagramm|Sequenzdiagramme]], [[UML_Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[UML_Zustandsdiagramm|Zustandsdiagramme]] besser. Es ist ungeeignet für nicht-objektorientierte [[Systeme]] oder wenn die [[Modellierung]] zu detailliert wird, sodass der [[Überblick]] verloren geht. Im Gegensatz zu [[Use-Case-Diagramm|Use-Case-Diagrammen]], die funktionale [[Anforderung|Anforderungen]] aus [[Nutzer|Nutzerperspektive]] beschreiben, konzentriert sich das Klassendiagramm auf die statische [[Struktur]] und [[Architektur]] eines [[System|Systems]]. Es unterscheidet sich zudem von [[Datenmodell|Datenmodellen]] wie [[Entity-Relationship-Diagramm|Entity-Relationship-Diagrammen]], da es nicht nur [[Datenstruktur|Datenstrukturen]], sondern auch [[Operation|Operationen]] und [[Verhalten]] abbildet. Für einfache [[Projekt|Projekte]] oder [[Prototyp|Prototypen]] kann der Aufwand der Erstellung den [[Nutzen]] übersteigen, da hier informelle Skizzen oder direkte [[Implementierung]] ausreichen. Bei übermäßiger [[Detaillierung]] besteht die Gefahr, dass das Diagramm unübersichtlich wird und seine primäre Funktion als [[Kommunikationsmittel]] verliert. Klassendiagramme ersetzen keinen [[Quellcode]], sondern dienen als [[Werkzeug]] zur [[Abstraktion]] und [[Kommunikation]] von [[Architekturentscheidung|Architekturentscheidungen]] auf konzeptioneller Ebene. Sie sind nicht geeignet für die Darstellung von [[Implementierungsdetail|Implementierungsdetails]] wie [[Algorithmus|Algorithmen]] oder konkreten [[Datenbankabfrage|Datenbankabfragen]]. Zudem besteht die Gefahr, bei zu früher Fokussierung auf technische [[Klasse|Klassen]] statt auf Konzepte der [[Problemdomäne]] Lösungsdetails vorzeitig festzulegen, was die [[Flexibilität]] des [[Design|Designs]] einschränken kann. Im Vergleich zu [[Paketdiagramm|Paketdiagrammen]] zeigen sie keine hierarchische Organisation von [[Modul|Modulen]], und gegenüber [[Komponentendiagramm|Komponentendiagrammen]] fehlt die Darstellung physischer [[Abhängigkeit|Abhängigkeiten]].
- **Beispiel / Code:** ```uml
class Mitglied {
    +name: String
    #alter: Date
    -adresse: Anschrift
    {static} leistung: Integer = 1
    +Mitglied(name: String, alter: Date)
    +{abstract} leistungsprognose(datum: Date): Integer
}

class Spieler {
    -nummer: Integer
    +vorstellen()
}

class Vereinsmitglied {
    +Vereinsmitglied(name: String, alter: Date)
    +leistungsprognose(datum: Date): Integer
}

class Abteilung {
    -name: String
    +Abteilung(name: String)
    +fuegeMitgliedHinzu(mitglied: Mitglied)
}

class Disziplin {
    -name: String
    +Disziplin(name: String)
}

class Ausuebung {
    -mitglied: Mitglied
    -disziplin: Disziplin
    -seit: LocalDate
    -ranking: Integer
    +Ausuebung(mitglied: Mitglied, disziplin: Disziplin, seit: LocalDate)
}

class MitgliedStatus {
    <<enumeration>>
    AKTIV
    PASSIV
    GESPERRT
}

Mitglied <|-- Spieler
Mitglied <|-- Vereinsmitglied
Mitglied "1" -- "*" Abteilung : gehört zu >
Mitglied "1" -- "*" Disziplin : übt aus >
Disziplin "1" -- "*" Mitglied : wird ausgeübt von >
Ausuebung .. Mitglied
Ausuebung .. Disziplin
```

```java
// Umsetzung des UML-Klassendiagramms in Java
public abstract class Mitglied {
    private String name;
    protected Date alter;
    private Anschrift adresse;
    static int leistung = 1;

    public Mitglied(String name, Date alter) {
        this.name = name;
        this.alter = alter;
    }

    public abstract int leistungsprognose(Date datum);
}

public class Vereinsmitglied extends Mitglied {
    public Vereinsmitglied(String name, Date alter) {
        super(name, alter);
    }

    @Override
    public int leistungsprognose(Date datum) {
        return Mitglied.leistung * 2;
    }
}

public class Spieler extends Mitglied {
    private int nummer;

    public Spieler(String name, Date alter, int nummer) {
        super(name, alter);
        this.nummer = nummer;
    }

    public void vorstellen() {
        System.out.println("Ich bin Spieler " + name + " mit der Nummer " + nummer);
    }

    @Override
    public int leistungsprognose(Date datum) {
        return Mitglied.leistung;
    }
}

public enum MitgliedStatus {
    AKTIV, PASSIV, GESPERRT
}

public class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;

    public Abteilung(String name) {
        this.name = name;
        this.mitglieder = new ArrayList<>();
    }

    public void fuegeMitgliedHinzu(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
}

public class Disziplin {
    private String name;

    public Disziplin(String name) {
        this.name = name;
    }
}

public class Ausuebung {
    private Mitglied mitglied;
    private Disziplin disziplin;
    private LocalDate seit;
    private int ranking;

    public Ausuebung(Mitglied mitglied, Disziplin disziplin, LocalDate seit) {
        this.mitglied = mitglied;
        this.disziplin = disziplin;
        this.seit = seit;
    }
}

// Beispiel eines Klassendiagramms als Java-Code umgesetzt
public class Mitglied {
    private String name;
    private int mitgliedsnummer;

    public Mitglied(String name, int mitgliedsnummer) {
        this.name = name;
        this.mitgliedsnummer = mitgliedsnummer;
    }

    public void beitreten(Verein verein) {
        verein.hinzufuegenMitglied(this);
    }
}

public class Verein {
    private String name;
    private List<Mitglied> mitglieder = new ArrayList<>();

    public Verein(String name) {
        this.name = name;
    }

    public void hinzufuegenMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d3
- **Vorgänger / Parent:** [[UML]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
