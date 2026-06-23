---
id: ba684d7d-d869-4ded-bc88-44fd121e773d
title: "Verhaltensmuster"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - design
  - verhalten
  - verhaltensmuster
  - architektur
  - draft
source: "software_engineering_kapitel_15"
---

# [[Verhaltensmuster]]

- **Kernkonzept:** [[Verhaltensmuster]] sind [[Entwurfsmuster]] in der [[objektorientierte_Programmierung|objektorientierten Softwareentwicklung]], die die [[Interaktion]] und [[Kommunikation]] zwischen [[Objekt|Objekten]] sowie die Zuweisung von [[Verantwortlichkeit|Verantwortlichkeiten]] regeln. Sie definieren standardisierte [[Steuerungslogik|Steuerungsabläufe]], um komplexe [[Aufgabe|Aufgaben]] flexibel und entkoppelt zu erfüllen, ohne die [[Kopplung]] zwischen [[Klasse|Klassen]] zu erhöhen. Dabei beschreiben sie, wie [[Objekt|Objekte]] zusammenarbeiten, um bestimmte [[Aufgabe|Aufgaben]] zu lösen, ohne ihre [[Implementierung]] fest zu koppeln.
- **Nutzen & Zweck:** [[Verhaltensmuster]] verbessern die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Verständlichkeit]] von [[Software]], indem sie [[Verantwortlichkeit|Verantwortlichkeiten]] klar verteilen und die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] fördern. Sie lösen wiederkehrende [[Problemstellung|Probleme]] in der dynamischen [[Interaktion]] von [[Objekt|Objekten]], wie die [[Entkopplung]] von [[Sender]] und [[Empfänger]] in der [[Kommunikation]] oder die flexible Steuerung von [[Algorithmus|Algorithmen]] zur Laufzeit. Besonders in [[Event-gesteuertes_System|Event-gesteuerten Systemen]] oder bei dynamischen [[Zustandsübergang|Zustandsübergängen]] schaffen sie klare Strukturen für [[Ablauf|Abläufe]] und [[Verantwortlichkeit|Verantwortlichkeiten]]. Dadurch wird der [[Code]] anpassungsfähiger an neue [[Anforderung|Anforderungen]] und leichter zu [[Refactoring|refaktorieren]], ohne die [[Softwarearchitektur]] grundlegend zu verändern. 

Sie optimieren die Zusammenarbeit zwischen [[Objekt|Objekten]] und ermöglichen eine dynamische Zuweisung von [[Verantwortlichkeit|Verantwortlichkeiten]], was die [[Kohäsion]] innerhalb der [[Komponente|Komponenten]] stärkt. Durch die Bereitstellung von Standardlösungen für häufig auftretende Verhaltensprobleme – wie die Steuerung von [[Algorithmus|Algorithmen]], die Verwaltung von [[Zustand|Zuständen]] oder die Koordination von [[Objektkommunikation]] – fördern sie zudem die [[Wiederverwendbarkeit]] von [[Code]]. Sie existieren, um die Flexibilität und [[Wartbarkeit]] von [[Software]] zu erhöhen, indem sie [[Zuständigkeit|Zuständigkeiten]] zwischen [[Objekt|Objekten]] klar trennen und die [[Kommunikation]] zwischen ihnen standardisieren.
- **Abgrenzung & Grenzen:** [[Verhaltensmuster]] sollten nicht eingesetzt werden, wenn die [[Problemstellung]] einfach, linear oder statisch ist, da der zusätzliche [[Abstraktionsaufwand]] den Nutzen übersteigt. Sie unterscheiden sich von [[Strukturmuster|Strukturmustern]] (z. B. [[Adapter_Pattern|Adapter]], [[Fassade_Pattern|Fassade]]), die die [[Komposition]] von [[Klasse|Klassen]] und [[Objekt|Objekten]] betreffen, und von [[Erzeugungsmuster|Erzeugungsmustern]] (z. B. [[Fabrikmethode_Pattern|Fabrikmethode]], [[Singleton_Pattern|Singleton]]), die die [[Objekterzeugung]] kapseln. [[Verhaltensmuster]] konzentrieren sich auf das *Wie* der Zusammenarbeit, nicht auf das *Was* oder *Wann*. 

In [[Performance-kritische_Anwendung|performancekritischen Anwendungen]] oder stark [[Datengetriebenes_System|datengetriebenen Systemen]] können sie unnötige [[Komplexität]] einführen, da sie oft zusätzliche [[Indirektion|Indirektionen]] oder [[Delegation|Delegationen]] erfordern. Zudem sind sie ungeeignet, wenn keine komplexen [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]] vorliegen oder die [[Steuerungslogik]] trivial ist. Direkte [[Methodenaufruf|Methodenaufrufe]] oder einfache [[Algorithmus|Algorithmen]] sind in solchen Fällen oft effizienter. Sie sind überdimensioniert, wenn nur einfache [[Delegation]] oder direkte [[Methodenaufruf|Methodenaufrufe]] ausreichen. 

[[Verhaltensmuster]] sind auch nicht geeignet, wenn eine starre, unveränderliche [[Softwarearchitektur]] bevorzugt wird, da sie auf dynamische Anpassungen ausgelegt sind. Sie sollten vermieden werden, wenn die [[Problemstellung]] keine komplexen [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]] erfordert, da sie zusätzlichen Overhead durch [[Abstraktion|Abstraktionen]] einführen.
- **Beispiel / Code:** ```java
// Beispiel: [[Observer_Pattern|Observer-Muster]] (ein klassisches [[Verhaltensmuster]])
interface Observer {
    void update(String message);
}

class NewsAgency {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void notifyObservers(String news) {
        for (Observer observer : observers) {
            observer.update(news);
        }
    }
}

class NewsChannel implements Observer {
    @Override
    public void update(String message) {
        System.out.println("Breaking News: " + message);
    }
}

// Alternative Implementierung mit generischem [[Subjekt]]
class Subject {
    private List<Observer> observers = new ArrayList<>();
    private String state;

    public void attach(Observer observer) {
        observers.add(observer);
    }

    public void setState(String state) {
        this.state = state;
        notifyObservers();
    }

    private void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(state);
        }
    }
}

class ConcreteObserver implements Observer {
    private String name;
    
    public ConcreteObserver(String name) {
        this.name = name;
    }
    
    @Override
    public void update(String message) {
        System.out.println(name + " received: " + message);
    }
}

// Nutzung:
NewsAgency agency = new NewsAgency();
agency.addObserver(new NewsChannel());
agency.notifyObservers("Neues [[Software_Engineering]]-Buch veröffentlicht!");

Subject subject = new Subject();
Observer observer1 = new ConcreteObserver("Observer 1");
Observer observer2 = new ConcreteObserver("Observer 2");
subject.attach(observer1);
subject.attach(observer2);
subject.setState("Neuer Zustand");

// Ergänzendes Beispiel: [[Strategy_Pattern|Strategy-Muster]] (ein weiteres [[Verhaltensmuster]])
interface PaymentStrategy {
    void pay(int amount);
}

class CreditCardPayment implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println("Bezahlt " + amount + " € per Kreditkarte.");
    }
}

class PayPalPayment implements PaymentStrategy {
    @Override
    public void pay(int amount) {
        System.out.println("Bezahlt " + amount + " € per PayPal.");
    }
}

class ShoppingCart {
    private PaymentStrategy paymentStrategy;

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

// Nutzung:
ShoppingCart cart = new ShoppingCart();
cart.setPaymentStrategy(new CreditCardPayment());
cart.checkout(100);
cart.setPaymentStrategy(new PayPalPayment());
cart.checkout(50);

// Beispiel: [[Observer_Pattern|Observer-Muster]] (Wetterstation)
import java.util.ArrayList;
import java.util.List;

class Wetterstation {
    private int temperatur;
    private List<Beobachter> beobachter = new ArrayList<>();

    public void registriereBeobachter(Beobachter b) {
        beobachter.add(b);
    }

    public void entferneBeobachter(Beobachter b) {
        beobachter.remove(b);
    }

    public void benachrichtigeBeobachter() {
        for (Beobachter b : beobachter) {
            b.aktualisiere(temperatur);
        }
    }

    public void setTemperatur(int temp) {
        this.temperatur = temp;
        benachrichtigeBeobachter();
    }
}

interface Beobachter {
    void aktualisiere(int temperatur);
}

class Anzeige implements Beobachter {
    @Override
    public void aktualisiere(int temperatur) {
        System.out.println("Aktuelle Temperatur: " + temperatur + "°C");
    }
}

// Nutzung:
public class Main {
    public static void main(String[] args) {
        Wetterstation station = new Wetterstation();
        Anzeige anzeige = new Anzeige();
        station.registriereBeobachter(anzeige);
        station.setTemperatur(25);
    }
}

// Beispiel: [[State_Pattern|State-Muster]] (erweitertes [[Verhaltensmuster]])
interface State {
    void handle(Context context);
}

class ConcreteStateA implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Zustand A: Aktion ausgeführt.");
        context.setState(new ConcreteStateB());
    }
}

class ConcreteStateB implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Zustand B: Aktion ausgeführt.");
        context.setState(new ConcreteStateA());
    }
}

class Context {
    private State state;

    public Context(State state) {
        this.state = state;
    }

    public void setState(State state) {
        this.state = state;
    }

    public void request() {
        state.handle(this);
    }
}

// Nutzung:
Context context = new Context(new ConcreteStateA());
context.request(); // Zustand A
context.request(); // Zustand B
```

Das [[Observer_Pattern|Observer-Muster]] demonstriert die [[Lose_Kopplung|lose Kopplung]] zwischen [[Beobachter|Beobachtern]] (z. B. `NewsChannel`, `ConcreteObserver`, `Anzeige`) und dem [[Subjekt]] (z. B. `NewsAgency`, `Subject`, `Wetterstation`). Änderungen am [[Subjekt]] erfordern keine Anpassungen der [[Beobachter|Beobachter]], was die [[Erweiterbarkeit]] und [[Wartbarkeit]] des Systems verbessert. Dieses [[Muster]] eignet sich besonders für [[Event-gesteuertes_System|Event-gesteuerte Systeme]], in denen [[Objekt|Objekte]] auf [[Zustandsänderung|Zustandsänderungen]] reagieren müssen, ohne direkt voneinander abhängig zu sein.

Das [[Strategy_Pattern|Strategy-Muster]] zeigt, wie [[Algorithmus|Algorithmen]] (z. B. Zahlungsmethoden) zur Laufzeit ausgetauscht werden können, ohne die [[Klasse]] des [[Kontext]] (hier `ShoppingCart`) zu ändern. Dies fördert die [[Flexibilität]] und [[Erweiterbarkeit]] des Systems, da neue [[Strategie|Strategien]] einfach hinzugefügt werden können.

Das [[State_Pattern|State-Muster]] ermöglicht es einem [[Objekt]], sein [[Verhalten]] zu ändern, wenn sich sein interner [[Zustand]] ändert. Es kapselt [[Zustand|Zustände]] in separate [[Klasse|Klassen]] und delegiert [[Zustandsübergang|Zustandsübergänge]] an diese, was die [[Kohäsion]] erhöht und die [[Komplexität]] reduziert.
