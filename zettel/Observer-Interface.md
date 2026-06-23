---
id: 5dfd7fbd-9d66-4f99-a6b9-e696669718d3
title: "Observer-Interface"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - beobachtung
  - interface
  - draft
source: "software_engineering_kapitel_12"
---

# [[Observer-Interface]]

- **Kernkonzept:** Das Observer-Interface ist ein zentrales Element des Observer-Design-Patterns, das eine lose Kopplung zwischen einem Subjekt (Observable) und seinen Beobachtern (Observers) ermöglicht. Es definiert eine Schnittstelle, über die Beobachter über Zustandsänderungen des Subjekts benachrichtigt werden, ohne dass das Subjekt deren konkrete Implementierung kennen muss.
- **Nutzen & Zweck:** Das Observer-Interface löst das Problem der dynamischen und flexiblen Benachrichtigung von abhängigen Objekten bei Zustandsänderungen eines zentralen Objekts. Es ermöglicht eine effiziente Kommunikation zwischen Komponenten in ereignisgesteuerten Systemen, wie z. B. in der Model-View-Controller-Architektur (MVC), wo Views bei Änderungen des Models automatisch aktualisiert werden müssen. Dadurch wird die Wartbarkeit und Erweiterbarkeit des Systems verbessert, da neue Beobachter hinzugefügt werden können, ohne das Subjekt zu modifizieren.
- **Abgrenzung & Grenzen:** Das Observer-Interface sollte nicht genutzt werden, wenn eine starke Kopplung zwischen Subjekt und Beobachtern erforderlich ist oder wenn die Anzahl der Beobachter sehr groß wird, da dies zu Performance-Problemen führen kann (z. B. durch häufige Benachrichtigungen). Alternativen wie Event-Busse oder direkte Methodenaufrufe können sinnvoller sein, wenn die Kommunikation zwischen Komponenten einfacher oder deterministischer gestaltet werden soll. Zudem ist das Pattern ungeeignet, wenn die Reihenfolge der Benachrichtigungen kritisch ist, da diese nicht garantiert wird.
- **Beispiel / Code:** ```java
public interface Observer {
    void update(State state);
}

public interface Subject {
    void attach(Observer observer);
    void detach(Observer observer);
    State getState();
}

public class StateMachineImpl implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private State currentState;

    @Override
    public void attach(Observer observer) {
        observers.add(observer);
        observer.update(currentState);
    }

    @Override
    public void detach(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public State getState() {
        return currentState;
    }

    public void setState(State newState) {
        currentState = newState;
        observers.forEach(observer -> observer.update(newState));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** [[Benachrichtigungsmechanismus]]
- **Folgezettel / Unterzettel:**
  - [[Update-Methode]]
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[Benachrichtigungsmechanismus]]
