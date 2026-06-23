---
id: 4f9faf61-7669-4c6b-badb-77f96bd7af23
title: "Observer_Pattern"
date: 2026-06-24
tags:
  - software_engineering
  - verhaltensmuster
  - design_pattern
  - ereignisbehandlung
  - architektur
  - entwurfsmuster
  - event_handling
  - communication
  - mvc
  - beobachtung
  - draft
source: "software_engineering_kapitel_15"
---

# [[Observer_Pattern]]

- **Kernkonzept:** Das [[Observer_Pattern]] ist ein [[Verhaltensmuster|Verhaltensmuster]], das eine [[Eins-zu-viele-Abhängigkeit]] zwischen [[Objekt|Objekten]] definiert, indem ein [[Subjekt]] eine Liste von [[Beobachter|Beobachtern]] verwaltet und diese automatisch über [[Zustandsänderung|Zustandsänderungen]] informiert. Es fördert die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und ist besonders relevant in [[Event-gesteuertes_System|Event-gesteuerten Systemen]] sowie im [[Model_View_Controller_Pattern|MVC-Muster]], da es dynamische [[Aktualisierung|Aktualisierungen]] ohne starre [[Abhängigkeit|Abhängigkeiten]] ermöglicht.
- **Nutzen & Zweck:** Das [[Observer_Pattern]] löst das [[Problem]] der manuellen Synchronisation zwischen [[Komponente|Komponenten]], die voneinander abhängig sind, ohne direkte [[Abhängigkeit|Abhängigkeiten]] zu schaffen. Es ermöglicht die automatische [[Benachrichtigung]] von [[Beobachter|Beobachtern]] über [[Zustandsänderung|Zustandsänderungen]] im [[Subjekt]], was die [[Erweiterbarkeit]] und [[Wartbarkeit]] des [[Systems]] verbessert. Besonders nützlich ist es in [[GUI]]-Aktualisierungen, [[Event-gesteuertes_System|Event-gesteuerten Systemen]] und [[MVC_Architektur|MVC-Architekturen]], da es dynamische [[Aktualisierung|Aktualisierungen]] ohne starre Bindungen an das [[Modell]] ermöglicht. Durch die Einführung einer indirekten [[Benachrichtigungsmechanik]] vermeidet es starre [[Abhängigkeit|Abhängigkeiten]] und unterstützt die unabhängige Entwicklung und Wartung von [[Komponente|Komponenten]]. Dies ist besonders vorteilhaft in interaktiven [[Anwendung|Anwendungen]] wie [[GUI|GUIs]] oder verteilten [[System|Systemen]], wo Änderungen in einem Teil des [[Systems]] andere Teile automatisch aktualisieren müssen. Im [[Model_View_Controller_Pattern|MVC-Muster]] sorgt es für eine konsistente Darstellung, indem [[View|Views]] über Änderungen im [[Modell]] informiert werden, ohne dass das [[Modell]] direkt von den [[View|Views]] abhängig ist. Das [[Muster]] löst zudem das Problem der losen Kopplung zwischen [[Objekt|Objekten]], die voneinander abhängig sind, aber unabhängig voneinander verändert oder erweitert werden sollen, und ermöglicht eine effiziente [[Benachrichtigung]] mehrerer [[Komponente|Komponenten]] über [[Zustandsänderung|Zustandsänderungen]], ohne dass das [[Subjekt]] die konkreten [[Beobachter|Beobachter]] kennen muss.
- **Abgrenzung & Grenzen:** Das [[Observer_Pattern]] kann zu [[Performance-Problemen]] führen, wenn zu viele [[Beobachter]] registriert sind oder [[Benachrichtigung|Benachrichtigungen]] zu häufig ausgelöst werden. Es ist nicht geeignet für [[Echtzeit-Systeme]] mit strengen [[Latenz|Latenzanforderungen]] oder [[System|Systeme]] mit statischen [[Daten]], bei denen keine [[Aktualisierung|Aktualisierungen]] benötigt werden. Zudem eignet es sich nicht für Szenarien, in denen eine direkte, synchrone [[Kommunikation]] zwischen [[Komponente|Komponenten]] erforderlich ist, da das [[Muster]] eine asynchrone [[Benachrichtigung]] impliziert. Die [[Komplexität]] der [[Beobachter]]-Verwaltung kann den Nutzen übersteigen, insbesondere in verteilten [[System|Systemen]], wo Alternativen wie ein [[Event_Bus]] oder das [[Mediator_Pattern]] besser skalieren. Das [[Muster]] unterscheidet sich von generischen [[Event-gesteuertes_System|Event-gesteuerten Systemen]] durch die explizite [[Beobachter]]-Registrierung. Es ist ungeeignet, wenn die [[Beobachter]] stark unterschiedliche [[Aktualisierungslogik|Aktualisierungslogiken]] benötigen, da dies die [[Implementierung]] unnötig verkompliziert. Bei einfachen [[System|Systemen]] mit wenigen [[Abhängigkeit|Abhängigkeiten]] kann der Overhead des [[Musters]] unnötig sein. Zudem garantiert das [[Observer_Pattern]] keine bestimmte Reihenfolge der [[Benachrichtigung|Benachrichtigungen]], was in Szenarien mit strikten [[Ablauf|Ablaufanforderungen]] problematisch sein kann. Alternativen wie [[Polling]] können sinnvoller sein, wenn [[Beobachter]] nur selten aktualisiert werden müssen. Das [[Muster]] sollte nicht genutzt werden, wenn die Anzahl der [[Beobachter|Beobachter]] sehr groß ist oder häufige [[Zustandsänderung|Zustandsänderungen]] auftreten, da dies zu [[Performance-Problemen]] führen kann. Es eignet sich weniger für Szenarien, in denen eine strikte Synchronisation oder transaktionale [[Konsistenz]] erforderlich ist.
- **Beispiel / Code:** ```java
// Generisches Beispiel für das [[Observer_Pattern]]
interface Beobachter {
    void aktualisieren(String nachricht);
}

class Subjekt {
    private List<Beobachter> beobachter = new ArrayList<>();
    
    void anmelden(Beobachter beobachter) {
        this.beobachter.add(beobachter);
    }
    
    void abmelden(Beobachter beobachter) {
        this.beobachter.remove(beobachter);
    }
    
    void benachrichtigen(String nachricht) {
        for (Beobachter b : beobachter) {
            b.aktualisieren(nachricht);
        }
    }
}

class KonkreterBeobachter implements Beobachter {
    @Override
    public void aktualisieren(String nachricht) {
        System.out.println("[[Beobachter|Beobachter]] erhielt: " + nachricht);
    }
}

// Beispiel für das [[Observer_Pattern]] im [[Model_View_Controller_Pattern|MVC-Muster]]
public interface Observer {
    void update();
    void update(State state);
}

public interface Subject {
    void attach(Observer observer);
    void detach(Observer observer);
    void notifyObservers();
}

public class ConcreteSubject implements Subject {
    private List<Observer> observers = new ArrayList<>();
    
    public void attach(Observer observer) {
        observers.add(observer);
    }
    
    public void detach(Observer observer) {
        observers.remove(observer);
    }
    
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update();
        }
    }
    
    public void setState(State state) {
        observers.forEach(obs -> obs.update(state));
    }
}

// Beispiel für eine [[Zustandsmaschine]] mit [[Observer_Pattern]]
public class StateMachineImpl implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private State currentState;

    public void attach(Observer obs) {
        observers.add(obs);
        obs.update(currentState);
    }

    public void detach(Observer obs) {
        observers.remove(obs);
    }

    public void notifyObservers() {
        observers.forEach(Observer::update);
    }

    public void setState(State newState) {
        currentState = newState;
        notifyObservers();
    }
}

// Subjekt (Observable) mit spezifischem Zustand
interface Subject {
    void attach(Observer observer);
    void detach(Observer observer);
    void notifyObservers();
}

class ConcreteSubject implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String state;

    public void attach(Observer observer) {
        observers.add(observer);
    }

    public void detach(Observer observer) {
        observers.remove(observer);
    }

    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(state);
        }
    }

    public void setState(String state) {
        this.state = state;
        notifyObservers();
    }
}

// Beobachter (Observer) mit spezifischer Implementierung
interface Observer {
    void update(String state);
}

class ConcreteObserver implements Observer {
    private String name;

    public ConcreteObserver(String name) {
        this.name = name;
    }

    public void update(String state) {
        System.out.println(name + " wurde benachrichtigt. Neuer Zustand: " + state);
    }
}

// Nutzung des [[Observer_Pattern]]
public class ObserverPatternDemo {
    public static void main(String[] args) {
        ConcreteSubject subject = new ConcreteSubject();
        Observer observer1 = new ConcreteObserver("[[Beobachter|Beobachter]] 1");
        Observer observer2 = new ConcreteObserver("[[Beobachter|Beobachter]] 2");

        subject.attach(observer1);
        subject.attach(observer2);
        subject.setState("Zustand A");
        subject.setState("Zustand B");
    }
}
```
