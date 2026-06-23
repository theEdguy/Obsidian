---
id: ae0d51bc-fb59-40f2-a93f-f9e4b9685f72
title: "Zustandsautomat"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - verhaltensmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[Zustandsautomat]]

- **Kernkonzept:** Ein Zustandsautomat (auch State Machine) ist ein Verhaltensmuster, das das Verhalten eines Systems durch definierte Zustände, Übergänge zwischen diesen Zuständen und Aktionen modelliert. Er ermöglicht die Steuerung komplexer Abläufe, indem er den aktuellen Zustand eines Objekts verwaltet und auf Ereignisse reagiert.
- **Nutzen & Zweck:** Der Zustandsautomat löst das Problem der unübersichtlichen und fehleranfälligen Steuerung von Systemen mit vielen möglichen Zuständen und Übergängen. Er bietet eine klare Struktur, um Zustandsabhängigkeiten zu kapseln, die Wartbarkeit zu erhöhen und sicherzustellen, dass sich ein System zu jedem Zeitpunkt in einem definierten Zustand befindet. Besonders nützlich ist er bei der Implementierung von Benutzeroberflächen, Protokollen oder Geschäftsprozessen, wo Zustandswechsel logisch und nachvollziehbar abgebildet werden müssen.
- **Abgrenzung & Grenzen:** Ein Zustandsautomat sollte nicht eingesetzt werden, wenn das System nur wenige oder einfache Zustände besitzt, da der Overhead der Implementierung den Nutzen übersteigt. Alternativen wie einfache Bedingungsprüfungen (if-else) oder das Strategie-Muster sind in solchen Fällen effizienter. Zudem ist ein Zustandsautomat ungeeignet, wenn Zustandsübergänge dynamisch zur Laufzeit erstellt oder verändert werden müssen, da dies die Komplexität stark erhöht. Im Vergleich zum Beobachter-Muster, das auf Ereignisse reagiert, ohne den Zustand explizit zu verwalten, bietet der Zustandsautomat eine strengere Kontrolle über den Systemzustand.
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
