---
id: 139699b2-11a8-46c3-ad75-01db94e2eafa
title: "Erzeugungsmuster"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - erzeugungsmuster
  - software_architecture
  - oop
  - design
  - erzeugung
  - architektur
  - draft
source: "software_engineering_kapitel_14"
---

# [[Erzeugungsmuster]]

- **Kernkonzept:** [[Erzeugungsmuster]] sind eine [[Kategorie]] von [[Entwurfsmuster|Entwurfsmustern]], die sich mit der [[Erzeugung|Erstellung]] von [[Objekt|Objekten]] befassen. Sie kapseln die [[Logik]] der [[Objekterzeugung]] und entkoppeln das [[System]] von der konkreten [[Implementierung]] der erzeugten [[Objekt|Objekte]], indem sie definierte [[Schnittstelle|Schnittstellen]] nutzen, ohne deren konkrete [[Klasse|Klassen]] zu kennen.
- **Nutzen & Zweck:** [[Erzeugungsmuster]] lösen das [[Problem]] der starren [[Abhängigkeit]] zwischen [[Client-Code|Klienten]] und konkreten [[Klasse|Klassen]], indem sie die [[Objekterzeugung]] zentralisieren und flexibilisieren. Sie fördern [[Lose_Kopplung|lose Kopplung]], [[Wiederverwendbarkeit]], [[Austauschbarkeit]] und [[Wartbarkeit]] von [[Code]], indem sie die [[Erzeugung]] von [[Objekt|Objekten]] von deren Nutzung trennen. Dadurch können [[System|Systeme]] leichter an neue [[Anforderung|Anforderungen]] angepasst werden, ohne bestehende [[Implementierung|Implementierungen]] zu ändern. Sie verbessern die [[Testbarkeit]] durch einfache [[Mocking|Mocks]] oder [[Ersatz]] von [[Abhängigkeit|Abhängigkeiten]] und ermöglichen die dynamische [[Instanziierung]] von [[Objekt|Objekten]] zur [[Laufzeit]]. Besonders nützlich sind sie in [[System|Systemen]], in denen [[Objekt|Objekte]] in verschiedenen [[Variante|Varianten]] oder [[Konfiguration|Konfigurationen]] benötigt werden, ohne den [[Client-Code]] anzupassen. Zudem reduzieren sie [[Redundanz]] und fördern [[Kohäsion]] durch die Zentralisierung des [[Erstellungsprozess|Erstellungsprozesses]].
- **Abgrenzung & Grenzen:** [[Erzeugungsmuster]] sind nicht universell einsetzbar und können zu [[Überkomplexität]] führen, wenn die [[Objekterzeugung]] trivial ist oder keine [[Variabilität]] erfordert. Im Vergleich zu direkten [[Konstruktor|Konstruktoren]] oder einfachen [[Fabrikmethode|Fabrikmethoden]] erhöhen sie die [[Komplexität]] des [[Codes]] und erfordern zusätzlichen [[Boilerplate-Code]]. Alternativen wie [[Dependency_Injection]] oder [[Refactoring]]-Techniken können ähnliche Ziele mit weniger Aufwand erreichen, insbesondere in kleinen [[Projekt|Projekten]] mit stabilen [[Anforderung|Anforderungen]]. Sie sind weniger geeignet in [[System|Systemen]], in denen die [[Objekterzeugung]] stark von unvorhersehbaren [[Laufzeit|Laufzeitbedingungen]] abhängt, da ihre [[Flexibilität]] möglicherweise nicht ausreicht. Zudem erschweren sie die Integration neuer [[Produkt|Produkttypen]], da alle beteiligten [[Fabrik|Fabriken]] angepasst werden müssen. Sie unterscheiden sich von [[Strukturmuster|strukturellen Mustern]] (z. B. [[Adapter]], [[Dekorierer]]), die [[Beziehung|Beziehungen]] zwischen [[Objekt|Objekten]] definieren, und von [[Verhaltensmuster|Verhaltensmustern]] (z. B. [[Strategie]], [[Beobachter]]), die das [[Verhalten]] von [[Objekt|Objekten]] steuern. Ihr Einsatz sollte immer durch eine [[Kosten-Nutzen-Analyse]] gerechtfertigt sein, um unnötigen Overhead zu vermeiden.
- **Beispiel / Code:** ```java
// Beispiel für [[Factory_Method]] (ein [[Erzeugungsmuster]])
interface Fahrzeug {
    void fahren();
}

class Auto implements Fahrzeug {
    @Override
    public void fahren() {
        System.out.println("Auto fährt");
    }
}

class Fahrrad implements Fahrzeug {
    @Override
    public void fahren() {
        System.out.println("Fahrrad fährt");
    }
}

class FahrzeugFactory {
    public Fahrzeug erstellen(String typ) {
        if (typ.equals("Auto")) {
            return new Auto();
        } else if (typ.equals("Fahrrad")) {
            return new Fahrrad();
        }
        throw new IllegalArgumentException("Unbekannter [[Fahrzeugtyp]]");
    }
}

// Nutzung
Fahrzeug fahrzeug = new FahrzeugFactory().erstellen("Auto");
fahrzeug.fahren();

// Beispiel für [[Singleton]] (ein weiteres [[Erzeugungsmuster]])
public class DatabaseConnection {
    private static DatabaseConnection instance;

    private DatabaseConnection() {}

    public static synchronized DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }
    
    public void connect() {
        System.out.println("Verbindung zur Datenbank hergestellt.");
    }
}

// Nutzung
DatabaseConnection connection = DatabaseConnection.getInstance();
connection.connect();

// Beispiel für [[Abstract_Factory]] (erweitertes [[Erzeugungsmuster]])
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

class WindowsFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new WindowsButton();
    }
    
    @Override
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

class MacOSFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new MacOSButton();
    }
    
    @Override
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}

interface Button {
    void paint();
}

class WindowsButton implements Button {
    @Override
    public void paint() {
        System.out.println("Windows-Button gerendert.");
    }
}

class MacOSButton implements Button {
    @Override
    public void paint() {
        System.out.println("macOS-Button gerendert.");
    }
}

interface Checkbox {
    void paint();
}

class WindowsCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Windows-Checkbox gerendert.");
    }
}

class MacOSCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("macOS-Checkbox gerendert.");
    }
}

// Nutzung
GUIFactory factory = new WindowsFactory();
Button button = factory.createButton();
Checkbox checkbox = factory.createCheckbox();
button.paint();
checkbox.paint();

// Beispiel für [[Abstract_Factory]] im Adressbuch-Kontext
interface LabelFactory {
    AddressLabel createAddressLabel();
    TelephoneLabel createTelephoneLabel();
}

class GermanLabelFactory implements LabelFactory {
    public AddressLabel createAddressLabel() {
        return new GermanAddressLabel();
    }
    public TelephoneLabel createTelephoneLabel() {
        return new GermanTelephoneLabel();
    }
}

// Nutzung im Adressbuch
class AddressBook {
    private LabelFactory factory;
    
    public AddressBook(LabelFactory factory) {
        this.factory = factory;
    }
    
    public BusinessCard createBusinessCard() {
        AddressLabel al = factory.createAddressLabel();
        TelephoneLabel tl = factory.createTelephoneLabel();
        return new BusinessCard(al, tl);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[Entwurfsmuster]]
- **Folgezettel / Unterzettel:**
  - [[Fabrikmethode]]
  - [[Abstrakte_Fabrik]]
  - [[Singleton]]
- **Querverweise:**
  - [[Erzeugungsprozess]]
  - [[Objekterzeugung]]
