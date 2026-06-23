---
id: 77aff846-8b82-4015-ba36-98a496a349c8
title: "Strukturmuster"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - design
  - struktur
  - strukturmuster
  - architektur
  - draft
source: "software_engineering_kapitel_15"
---

# [[Strukturmuster]]

- **Kernkonzept:** Strukturmuster sind [[Entwurfsmuster]] im [[Software_Engineering]], die sich mit der Komposition von [[Klasse|Klassen]] und [[Objekt|Objekten]] befassen, um größere [[Struktur|Strukturen]] zu bilden und die [[Zusammenarbeit]] zwischen [[Komponente|Komponenten]] zu vereinfachen. Sie definieren klare Regeln für die [[Interaktion]] zwischen [[Objekt|Objekten]] und [[Klasse|Klassen]], um [[Flexibilität]], [[Erweiterbarkeit]] und [[Wartbarkeit]] der [[Systemarchitektur]] zu gewährleisten, ohne deren [[Implementierung]] zu verändern. Durch die Anwendung von Mustern wie [[Adapter]], [[Decorator]], [[Fassade]] oder [[Bridge]] helfen sie, Beziehungen zwischen [[Entität|Entitäten]] so zu gestalten, dass sie modular, anpassbar und wiederverwendbar bleiben.
- **Nutzen & Zweck:** Strukturmuster existieren, um die [[Komplexität]] von [[Software-System|Software-Systemen]] zu reduzieren, indem sie wiederverwendbare [[Lösungsmuster]] für häufige [[Designproblem|Designprobleme]] bei der Strukturierung von [[Klasse|Klassen]] und [[Objekt|Objekten]] bieten. Sie lösen konkrete Probleme wie starre [[Abhängigkeit|Abhängigkeiten]] zwischen [[Komponente|Komponenten]], unnötige [[Redundanz|Redundanzen]], ineffiziente [[Objektkomposition|Objektkompositionen]] oder erschwerte [[Erweiterbarkeit]], indem sie bewährte Techniken wie [[Komposition]], [[Delegation]], [[Schnittstellenstandardisierung]] oder die Entkopplung von [[Abstraktion]] und [[Implementierung]] einführen. Dadurch ermöglichen sie eine klare [[Trennung_von_Verantwortlichkeiten]], fördern die [[Wiederverwendbarkeit]] von [[Code]], verbessern die [[Anpassungsfähigkeit]] an sich ändernde [[Anforderung|Anforderungen]] und tragen zur [[Lose_Kopplung|losen Kopplung]] sowie [[Hohe_Kohäsion|hohen Kohäsion]] bei. Dies erhöht die [[Skalierbarkeit]], [[Testbarkeit]] und [[Wartbarkeit]] des Systems, ohne die [[Performance]] unnötig zu beeinträchtigen. Zudem vereinfachen sie die Integration neuer [[Funktionalität|Funktionalitäten]] und die [[Wiederverwendung]] bestehender [[Komponente|Komponenten]], insbesondere in komplexen Systemen mit vielen [[Abhängigkeit|Abhängigkeiten]]. Strukturmuster helfen dabei, starre [[Kopplung]] oder unflexible Anpassungen an neue [[Anforderung|Anforderungen]] zu vermeiden und schaffen klare, erweiterbare [[Struktur|Strukturen]].
- **Abgrenzung & Grenzen:** Strukturmuster sollten nicht eingesetzt werden, wenn die [[Problemstellung]] keine komplexen [[Objektbeziehung|Objektbeziehungen]] oder [[Klassenbeziehung|Klassenbeziehungen]] erfordert oder wenn eine einfachere Lösung ohne [[Entwurfsmuster]] ausreicht. Im Vergleich zu [[Verhaltensmuster|Verhaltensmustern]], die sich auf die [[Kommunikation]] und [[Interaktion]] zwischen [[Objekt|Objekten]] konzentrieren, oder [[Erzeugungsmuster|Erzeugungsmustern]], die die [[Objekterzeugung]] steuern, adressieren Strukturmuster ausschließlich die statische [[Struktur]] eines Systems. Sie sind ungeeignet, wenn dynamische [[Verhaltensänderung|Verhaltensänderungen]] im Vordergrund stehen oder wenn die [[Performance]] durch zusätzliche [[Abstraktion|Abstraktionsebenen]] kritisch beeinträchtigt wird. Ein übermäßiger Einsatz kann zu [[Over-Engineering]] führen, da sie zusätzliche [[Komplexität]] einführen, die bei einfachen [[Problemstellung|Problemstellungen]] nicht gerechtfertigt ist. Zudem sind sie nicht notwendig, wenn die gewünschte [[Flexibilität]] bereits durch einfache [[Assoziation|Assoziationen]], [[Aggregation|Aggregationen]] oder [[Komposition]] erreicht werden kann. Strukturmuster können die [[Lesbarkeit]] des [[Code|Codes]] verschlechtern, wenn sie unnötig eingesetzt werden oder wenn die gewählte [[Struktur]] die Verständlichkeit beeinträchtigt. Besonders in Systemen mit kritischen [[Performance|Performance-Anforderungen]] sollte der Einsatz sorgfältig abgewogen werden, da zusätzliche Schichten oder [[Delegation|Delegationen]] die Laufzeit negativ beeinflussen können. Sie sind auch keine Lösung für Probleme, die besser durch algorithmische Optimierungen oder Änderungen der [[Datenstruktur|Datenstrukturen]] gelöst werden können.
- **Beispiel / Code:** ```java
// Beispiel 1: Adapter-Muster (Anpassung inkompatibler [[Schnittstelle|Schnittstellen]])
interface ZielSchnittstelle {
    void erwarteteMethode();
}

class Adaptee {
    void spezifischeMethode() {
        System.out.println("Spezifische Methode des Adaptee wird aufgerufen.");
    }
}

class Adapter implements ZielSchnittstelle {
    private Adaptee adaptee;
    
    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    
    @Override
    public void erwarteteMethode() {
        adaptee.spezifischeMethode();
    }
}

public class Main {
    public static void main(String[] args) {
        Adaptee adaptee = new Adaptee();
        ZielSchnittstelle adapter = new Adapter(adaptee);
        adapter.erwarteteMethode(); // Ruft die spezifische Methode des Adaptee auf
    }
}

// Beispiel 2: Adapter-Muster (Anpassung einer alten Datenbank-[[Schnittstelle]])
class AlteDatenbank {
    public void speichereDatenAlt(String daten) {
        System.out.println("Daten in alter Datenbank gespeichert: " + daten);
    }
}

interface Datenbank {
    void speichereDaten(String daten);
}

class DatenbankAdapter implements Datenbank {
    private AlteDatenbank alteDatenbank;
    
    public DatenbankAdapter(AlteDatenbank alteDatenbank) {
        this.alteDatenbank = alteDatenbank;
    }
    
    @Override
    public void speichereDaten(String daten) {
        alteDatenbank.speichereDatenAlt(daten);
    }
}

public class MainAdapter {
    public static void main(String[] args) {
        AlteDatenbank alteDb = new AlteDatenbank();
        Datenbank db = new DatenbankAdapter(alteDb);
        db.speichereDaten("Testdaten");
    }
}

// Beispiel 3: Decorator-Muster (dynamische Erweiterung von [[Objekt|Objekten]] zur Laufzeit)
abstract class Kaffee {
    abstract double getKosten();
    abstract String getBeschreibung();
}

class EinfacherKaffee extends Kaffee {
    @Override
    double getKosten() {
        return 1.0;
    }
    
    @Override
    String getBeschreibung() {
        return "Einfacher Kaffee";
    }
}

abstract class KaffeeDecorator extends Kaffee {
    protected Kaffee kaffee;
    
    public KaffeeDecorator(Kaffee kaffee) {
        this.kaffee = kaffee;
    }
}

class MilchDecorator extends KaffeeDecorator {
    public MilchDecorator(Kaffee kaffee) {
        super(kaffee);
    }
    
    @Override
    double getKosten() {
        return kaffee.getKosten() + 0.5;
    }
    
    @Override
    String getBeschreibung() {
        return kaffee.getBeschreibung() + ", mit Milch";
    }
}

class ZuckerDecorator extends KaffeeDecorator {
    public ZuckerDecorator(Kaffee kaffee) {
        super(kaffee);
    }
    
    @Override
    double getKosten() {
        return kaffee.getKosten() + 0.2;
    }
    
    @Override
    String getBeschreibung() {
        return kaffee.getBeschreibung() + ", mit Zucker";
    }
}

// Nutzung des Decorator-Musters:
public class MainDecorator {
    public static void main(String[] args) {
        Kaffee meinKaffee = new ZuckerDecorator(new MilchDecorator(new EinfacherKaffee()));
        System.out.println(meinKaffee.getBeschreibung()); // "Einfacher Kaffee, mit Milch, mit Zucker"
        System.out.println(meinKaffee.getKosten()); // 1.7
    }
}

// Beispiel 4: Fassade-Muster (Vereinfachung komplexer [[Schnittstelle|Schnittstellen]])
class CPU {
    public void start() {
        System.out.println("CPU gestartet");
    }
}

class Memory {
    public void load() {
        System.out.println("Speicher geladen");
    }
}

class HardDrive {
    public void read() {
        System.out.println("Festplatte liest Daten");
    }
}

class ComputerFassade {
    private CPU cpu;
    private Memory memory;
    private HardDrive hardDrive;
    
    public ComputerFassade() {
        this.cpu = new CPU();
        this.memory = new Memory();
        this.hardDrive = new HardDrive();
    }
    
    public void startComputer() {
        cpu.start();
        memory.load();
        hardDrive.read();
        System.out.println("Computer erfolgreich gestartet");
    }
}

public class MainFassade {
    public static void main(String[] args) {
        ComputerFassade computer = new ComputerFassade();
        computer.startComputer();
    }
}

// Beispiel 5: Bridge-Muster (Entkopplung von [[Abstraktion]] und [[Implementierung]])
interface Implementierung {
    void operationImpl();
}

class KonkreteImplA implements Implementierung {
    public void operationImpl() {
        System.out.println("Konkrete Implementierung A");
    }
}

abstract class Abstraktion {
    protected Implementierung implementierung;
    
    public Abstraktion(Implementierung impl) {
        this.implementierung = impl;
    }
    
    public abstract void operation();
}

class VerfeinerteAbstraktion extends Abstraktion {
    public VerfeinerteAbstraktion(Implementierung impl) {
        super(impl);
    }
    
    public void operation() {
        implementierung.operationImpl();
    }
}

// Nutzung des Bridge-Musters:
public class MainBridge {
    public static void main(String[] args) {
        Abstraktion abstraktion = new VerfeinerteAbstraktion(new KonkreteImplA());
        abstraktion.operation();
    }
}
```
