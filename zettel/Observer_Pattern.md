---
aliases:
- Observer
date: 2026-05-30
id: 7d3d1da1-1a3c-4fd1-996d-e63353bff27e
source: SWE Slides (Folien 376-388)
tags:
- software_engineering
- verhaltensmuster
- design_pattern
- ereignisbehandlung
- architektur
- entwurfsmuster
- event_handling
- draft
title: Observer_Pattern
---

# [[Observer_Pattern]]

- **Kernkonzept:** Das [[Observer_Pattern]] ist ein [[Verhaltensmuster|Verhaltensmuster]], das eine [[Eins-zu-viele-Abhängigkeit]] zwischen [[Objekt|Objekten]] definiert, indem ein [[Subjekt]] eine Liste von [[Beobachter|Beobachtern]] verwaltet und diese automatisch über [[Zustandsänderung|Zustandsänderungen]] informiert. Es fördert die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] und ist besonders relevant in [[Event-gesteuertes_System|Event-gesteuerten Systemen]] sowie im [[Model_View_Controller_Pattern|MVC-Muster]].
- **Nutzen & Zweck:** Das [[Observer_Pattern]] löst das [[Problem]] der manuellen Synchronisation zwischen [[Komponente|Komponenten]], die voneinander abhängig sind, ohne direkte [[Abhängigkeit|Abhängigkeiten]] zu schaffen. Es ermöglicht die automatische [[Benachrichtigung]] von [[Beobachter|Beobachtern]] über [[Zustandsänderung|Zustandsänderungen]] im [[Subjekt]], was die [[Erweiterbarkeit]] und [[Wartbarkeit]] des [[Systems]] verbessert. Besonders nützlich ist es in [[GUI]]-Aktualisierungen, [[Event-gesteuertes_System|Event-gesteuerten Systemen]] und [[MVC_Architektur|MVC-Architekturen]], da es dynamische [[Aktualisierung|Aktualisierungen]] ohne starre Bindungen an das [[Modell]] ermöglicht.
- **Abgrenzung & Grenzen:** Das [[Observer_Pattern]] kann zu [[Performance-Problemen]] führen, wenn zu viele [[Beobachter]] registriert sind oder [[Benachrichtigung|Benachrichtigungen]] zu häufig ausgelöst werden. Es ist nicht geeignet für [[Echtzeit-Systeme]] mit strengen [[Latenz|Latenzanforderungen]] oder [[System|Systeme]] mit statischen [[Daten]], bei denen keine [[Aktualisierung|Aktualisierungen]] benötigt werden. Zudem eignet es sich nicht für Szenarien, in denen eine direkte, synchrone [[Kommunikation]] zwischen [[Komponente|Komponenten]] erforderlich ist. Die [[Komplexität]] der [[Beobachter|Beobachter]]-Verwaltung kann den Nutzen übersteigen, insbesondere in verteilten [[System|Systemen]], wo Alternativen wie ein [[Event_Bus]] oder das [[Mediator_Pattern]] besser skalieren. Es unterscheidet sich von generischen [[Event-gesteuertes_System|Event-gesteuerten Systemen]] durch die explizite [[Beobachter|Beobachter]]-Registrierung.
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
    
    public void attach(Observer obs) {
        observers.add(obs);
    }
    
    public void detach(Observer obs) {
        observers.remove(obs);
    }
    
    public void notifyObservers() {
        observers.forEach(Observer::update);
    }
    
    public void setState(State state) {
        observers.forEach(obs -> obs.update(state));
    }
}
```
