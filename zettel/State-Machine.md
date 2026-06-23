---
id: e5b6c6a9-d740-4ef6-91aa-f680730e70c5
title: "State-Machine"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - verhaltensmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[State-Machine]]

- **Kernkonzept:** Eine State-Machine (Zustandsmaschine) ist ein Verhaltensmuster, das das Verhalten eines Objekts durch definierte Zustände, Übergänge zwischen diesen Zuständen und Aktionen bei Zustandswechseln modelliert. Sie kapselt die Logik zur Verwaltung von Zuständen und deren Übergängen, um komplexe Steuerungsabläufe strukturiert abzubilden.
- **Nutzen & Zweck:** Die State-Machine löst das Problem der unübersichtlichen und fehleranfälligen Steuerung von Objekten mit vielen möglichen Zuständen und Übergängen. Sie ermöglicht eine klare Trennung von Zustandslogik und Geschäftslogik, verbessert die Wartbarkeit und reduziert die Komplexität durch zentrale Verwaltung der Zustandsübergänge. Besonders nützlich ist sie in Systemen mit definierten Abläufen, wie Benutzeroberflächen, Protokollimplementierungen oder Workflow-Management.
- **Abgrenzung & Grenzen:** Eine State-Machine sollte nicht eingesetzt werden, wenn das System nur wenige oder statische Zustände besitzt, da der Overhead der Implementierung den Nutzen übersteigt. Alternativen wie einfache Bedingungslogik (if-else) oder Strategie-Muster sind in solchen Fällen effizienter. Zudem ist das Muster ungeeignet, wenn Zustandsübergänge dynamisch zur Laufzeit definiert werden müssen, da dies die Struktur der State-Machine aufbricht. Im Vergleich zum Observer-Muster, das Zustandsänderungen lediglich propagiert, bietet die State-Machine eine aktive Steuerung der Übergänge.
- **Beispiel / Code:** ```java
public interface StateMachine {
    void attach(Observer obs);
    void detach(Observer obs);
    State getState();
    void setState(State state);
}

public class StateMachineImpl implements StateMachine, Subject {
    private List<Observer> observers = new ArrayList<>();
    private State currentState;

    public StateMachineImpl() {
        this.currentState = State.S_LOGIN;
    }

    @Override
    public void attach(Observer obs) {
        this.observers.add(obs);
        obs.update(currentState);
    }

    @Override
    public void detach(Observer obs) {
        this.observers.remove(obs);
    }

    @Override
    public State getState() {
        return this.currentState;
    }

    @Override
    public void setState(State state) {
        this.currentState = state;
        observers.forEach(obs -> obs.update(state));
    }
}
```
