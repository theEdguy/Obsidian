---
id: 91696e6d-d655-42e4-a6f9-b4d16ca7184f
title: "UML"
date: 2026-06-24
tags:
  - software_engineering
  - modellierungssprache
  - uml
  - modellierung
  - sprache
  - standard
  - draft
source: "software_engineering_kapitel_15"
---

# [[UML]]

- **Kernkonzept:** UML (Unified Modeling Language) ist eine standardisierte [[Modellierungssprache|Modellierungssprache]] zur [[Spezifikation]], Visualisierung, Konstruktion und Dokumentation von [[Software-System|Software-Systemen]], insbesondere im [[Objektorientierung|objektorientierten]] Kontext. Sie ermöglicht die Beschreibung struktureller und verhaltensbezogener Aspekte durch verschiedene [[Diagrammtyp|Diagrammtypen]] wie [[Klassendiagramm|Klassendiagramme]], [[Use-Case-Diagramm|Use-Case-Diagramme]], [[Sequenzdiagramm|Sequenzdiagramme]] oder [[Aktivitätsdiagramm|Aktivitätsdiagramme]] und unterstützt die methodische Durchgängigkeit von der [[Anforderungsanalyse]] bis zur [[Implementierung]].
- **Nutzen & Zweck:** UML existiert, um die [[Komplexität]] von [[Software-System|Software-Systemen]] beherrschbar zu machen und die Kommunikation zwischen [[Entwickler|Entwicklern]], [[Software-Architekt|Architekten]], [[Analyst|Analysten]] und [[Stakeholder|Stakeholdern]] zu vereinfachen. Sie löst das Problem der Mehrdeutigkeit in der [[Software-Entwicklung]] durch eine einheitliche Notation, die klare visuelle Darstellungen von [[Systemarchitektur|Systemarchitekturen]], [[Beziehung|Beziehungen]], Prozessen und [[Ablauf|Abläufen]] ermöglicht. Dadurch werden [[Qualität]] und [[Konsistenz]] des Systems verbessert, die [[Wartbarkeit]] sowie [[Dokumentation]] effizienter gestaltet, die [[Modularisierung]] gefördert und die Anwendung von [[Entwurfsmuster|Entwurfsmustern]] wie [[Observer_Pattern|Observer]] oder [[Fassade|Fassade]] unterstützt. UML ergänzt [[Agile_Methoden|agile Methoden]] sowie iterative [[Entwicklungsprozess|Entwicklungsprozesse]] und reduziert Missverständnisse durch strukturierte visuelle [[Modellierung]]. Zudem erleichtert sie die Planung, Analyse und Dokumentation komplexer [[Anforderung|Anforderungen]], was die Entwicklung und [[Wartung]] von Systemen beschleunigt und die [[Zusammenarbeit]] zwischen verschiedenen [[Rolle|Rollen]] im [[Projekt]] verbessert. Durch die Bereitstellung einer gemeinsamen visuellen Sprache wird die Kommunikation zwischen allen Beteiligten vereinfacht, was die Effizienz und Fehleranfälligkeit in der Analyse, Planung und Umsetzung von [[Software-Projekt|Software-Projekten]] reduziert. Besonders in heterogenen Teams oder bei der Zusammenarbeit mit nicht-technischen [[Stakeholder|Stakeholdern]] dient UML als Brücke, um [[Anforderung|Anforderungen]] präzise zu erfassen und [[Systemverhalten]] frühzeitig zu validieren. Sie standardisiert die Darstellung von [[Schnittstelle|Schnittstellen]], [[Abhängigkeit|Abhängigkeiten]] und [[Interaktion|Interaktionen]], was die [[Integration]] verschiedener Systemkomponenten erleichtert und die [[Wiederverwendbarkeit]] von [[Modul|Modulen]] fördert. UML ermöglicht eine frühzeitige Erkennung von [[Designfehler|Designfehlern]] und unterstützt die Wiederverwendbarkeit von Entwürfen durch standardisierte Notationen. Darüber hinaus fördert UML die strukturierte Planung vor der [[Implementierung]] und erleichtert die Analyse von [[Systemanforderung|Systemanforderungen]], was zu einer verbesserten [[Kohäsion]] und [[Lose_Kopplung|losen Kopplung]] im Design führt.
- **Abgrenzung & Grenzen:** UML sollte nicht genutzt werden, wenn detaillierte [[Implementierungsdetail|Implementierungsdetails]] oder spezifische [[Programmiersprache|Programmiersprachen]]-Konstrukte abgebildet werden müssen, da sie sich auf eine abstrakte [[Modellebene]] konzentriert und keine [[Programmiersprache]] ersetzt. Sie ist weniger geeignet für nicht-objektorientierte [[Software-System|Systeme]], [[Hardware]]-Modellierung oder wenn der Modellierungsaufwand den Nutzen übersteigt, z. B. bei sehr kleinen oder einfachen [[Projekt|Projekten]]. Alternativen wie informelle Skizzen, textuelle [[Spezifikation|Spezifikationen]], [[Domänenspezifische_Sprache|domänenspezifische Sprachen]] (DSLs), [[Flussdiagramm|Flussdiagramme]] oder [[Datenflussdiagramm|Datenflussdiagramme]] können in solchen Fällen effizienter sein. Zudem erfordert UML eine präzise Einhaltung der Notationsregeln, was zusätzlichen [[Lernaufwand]] bedeutet. Im Vergleich zu [[Ad-hoc-Modellierung|Ad-hoc-Modellierungen]] bietet UML zwar mehr [[Präzision]], kann aber bei übermäßiger Anwendung zu [[Over-Engineering]] führen. UML ersetzt keine [[Agile_Methoden|agilen Methoden]], sondern ergänzt diese durch strukturierte visuelle Modelle. Besonders in [[Projekt|Projekten]] mit schnellen Iterationen können informelle [[Diagramm|Diagramme]] oder Code-Prototypen ausreichen. Für die Modellierung von [[Geschäftsprozess|Geschäftsprozessen]] eignen sich Alternativen wie [[BPMN]] besser, während UML primär für [[Software-System|Software-Systeme]] konzipiert ist. Bei [[Echtzeitsystem|Echtzeitsystemen]] oder stark prozessorientierten Anwendungen können spezifischere Notationen wie [[SysML]] besser geeignet sein. UML ist keine Entwicklungsumgebung oder ein Debugging-Tool und sollte nicht als Ersatz für diese verwendet werden. Zudem stößt UML an Grenzen, wenn es um die Darstellung von [[Nebenläufigkeit|nebenläufigen]] oder [[Verteilte_System|verteilten Systemen]] mit komplexen [[Synchronisation|Synchronisationsmechanismen]] geht, da hier oft zusätzliche textuelle [[Spezifikation|Spezifikationen]] oder formale Methoden erforderlich sind. Für die direkte [[Codegenerierung]] sind zusätzliche Werkzeuge notwendig, da UML selbst keine ausführbaren Artefakte erzeugt. UML sollte vermieden werden, wenn die [[Komplexität]] des Systems gering ist und informelle Skizzen oder textuelle Beschreibungen ausreichen. Eine übermäßige Anwendung von UML kann zu unnötigem Overhead führen, insbesondere wenn die [[Diagramm|Diagramme]] nicht regelmäßig gepflegt werden. Bei stark algorithmischen oder prozeduralen Problemen sind Alternativen wie [[Pseudocode]] oder [[Flussdiagramm|Flussdiagramme]] oft besser geeignet.
- **Beispiel / Code:** ```java
// Beispiel eines UML-Klassendiagramms als Java-Code-Äquivalent mit zusätzlicher textueller Notation
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistung;
    private List<Disziplin> disziplinen;
    private String mitgliedsnummer;
    private String status;
    private Date beitrittsdatum;

    public Mitglied(String name, String adresse, int alter, String mitgliedsnummer) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        this.mitgliedsnummer = mitgliedsnummer;
        this.disziplinen = new ArrayList<>();
    }

    public int leistungsprognose() {
        return this.leistung * 2; // Beispielhafte Berechnung
    }

    public void hinzufuegenDisziplin(Disziplin disziplin) {
        disziplinen.add(disziplin);
    }

    public void abteilungVerlassen(Abteilung abteilung) {
        // Logik zur Entfernung aus der Abteilung
    }

    public void beitreten() {
        // Logik für Beitritt
    }

    public void austreten() {
        // Logik für Austritt
    }

    public String getMitgliedsdaten() {
        return "Mitgliedsnummer: " + mitgliedsnummer + ", Name: " + name;
    }

    public void aktualisiereDaten(String name) {
        this.name = name;
    }
}

class Disziplin {
    // Keine Referenz zurück zu Mitglied (navigierbare [[Assoziation]])
}

// Beispiel einer Komposition (existenzabhängige Teile)
class Buch {
    private List<Kapitel> kapitel;

    public Buch() {
        kapitel = new ArrayList<>();
    }

    public void hinzufuegenKapitel(Kapitel k) {
        kapitel.add(k); // Kapitel existiert nur im Kontext des Buchs
    }
}

class Kapitel {
    // Existenz abhängig vom Buch (Komposition)
}

class Abteilung {
    private String bezeichnung;
    private List<Mitglied> mitglieder;
}

class Verein {
    private String name;
    private List<Mitglied> mitglieder;
    private List<Abteilung> abteilungen;

    public Verein(String name) {
        this.name = name;
        this.mitglieder = new ArrayList<>();
        this.abteilungen = new ArrayList<>();
    }

    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }

    public boolean entfernenMitglied(String mitgliedsnummer) {
        return mitglieder.removeIf(m -> m.getMitgliedsdaten().contains(mitgliedsnummer));
    }
}

// Beispiel für eine [[Fassade|Fassade]]-Implementierung in UML (Java-Code)
public interface ManagementFactory {
    ManagementFactory FACTORY = new ManagementFacade();
    MemberManagement memberManagement();
}

@Component
@ApplicationScope
public class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    // Weitere Methoden zur Kapselung komplexer Interaktionen
}

// Beispiel: UML-Klassendiagramm als Java-Code (vereinfacht)
public class Adresse {
    private String strasse;
    private String hausnummer;
    private String postleitzahl;
    private String ort;
    
    public Adresse(String strasse, String hausnummer, String postleitzahl, String ort) {
        this.strasse = strasse;
        this.hausnummer = hausnummer;
        this.postleitzahl = postleitzahl;
        this.ort = ort;
    }
    
    public String getVollstaendigeAdresse() {
        return strasse + " " + hausnummer + ", " + postleitzahl + " " + ort;
    }
}

// Beziehung: Adressbuch enthält mehrere Adressen (1..*)
public class Adressbuch {
    private List<Adresse> adressen;
    
    public void hinzufuegen(Adresse adresse) {
        adressen.add(adresse);
    }
}

// Beispiel aus neuem Konzept: UML-Klassendiagramm für Verschlüsselung
public abstract class Cipher {
    public abstract void setKey(String key);
    public abstract byte[] encrypt(byte[] data);
    public abstract byte[] decrypt(byte[] data);
}

public class AESCipher extends Cipher {
    @Override
    public void setKey(String key) {
        // Implementierung der Schlüsselinitialisierung
    }
    
    @Override
    public byte[] encrypt(byte[] data) {
        // AES-Verschlüsselungslogik
        return new byte[0];
    }
    
    @Override
    public byte[] decrypt(byte[] data) {
        // AES-Entschlüsselungslogik
        return new byte[0];
    }
}
```

```uml
@startuml
left to right direction
actor Vereinsmanager
rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Mitglied löschen" as UC4
}
Vereinsmanager --> UC1
UC1 <|-- UC2
UC1 <|-- UC3
UC1 <|-- UC4

class Mitglied {
  -mitgliedsnummer: String
  -name: String
  -adresse: String
  -alter: Integer
  -leistung: Integer
  -status: String
  -beitrittsdatum: Date
  -disziplinen: List<Disziplin>
  +leistungsprognose(): Integer
  +hinzufuegenDisziplin(disziplin: Disziplin)
  +abteilungVerlassen(abteilung: Abteilung)
  +beitreten()
  +austreten()
  +getMitgliedsdaten(): String
  +aktualisiereDaten(name: String)
}

class Verein {
  -name: String
  -mitglieder: List<Mitglied>
  -abteilungen: List<Abteilung>
  +mitgliedHinzufuegen(mitglied: Mitglied)
  +entfernenMitglied(id: String)
}

class Cipher {
  +{abstract} setKey(key: String)
  +{abstract} encrypt(data: byte[]): byte[]
  +{abstract} decrypt(data: byte[]): byte[]
}

class AESCipher {
  +setKey(key: String)
  +encrypt(data: byte[]): byte[]
  +decrypt(data: byte[]): byte[]
}

Cipher <|-- AESCipher
Mitglied "1" -- "*" Verein : > gehört zu
Mitglied "*" -- "*" Abteilung
Buch "1" *-- "*" Kapitel : Komposition

participant "Objekt A" as A
participant "Objekt B" as B
A -> B: operation()
activate B
B --> A: Rückgabewert
deactivate B
@enduml
```

// UML-Notation für die Klasse 'Mitglied' (textuell beschrieben):
// Klasse: Mitglied
// Attribute:
// - mitgliedsnummer: String
// - name: String
// - adresse: String
// - alter: Integer
// - leistung: Integer
// - status: String
// - beitrittsdatum: Date
// - disziplinen: List<Disziplin> (binäre [[Assoziation]])
// Operationen:
// + leistungsprognose(): Integer
// + hinzufuegenDisziplin(disziplin: Disziplin): void
// + abteilungVerlassen(abteilung: Abteilung): void
// + beitreten(): void
// + austreten(): void
// + getMitgliedsdaten(): String
// + aktualisiereDaten(name: String): void
// Assoziationen:
// - Verein "1" -- "*" Mitglied
// - Mitglied "*" -- "*" Abteilung (z. B. für Abteilungszugehörigkeit)
// - Buch "1" *-- "*" Kapitel (Komposition)
