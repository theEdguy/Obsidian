---
id: a9050570-ac60-48c2-9aad-ce01c95ba3a3
title: "Model_View_Controller_(MVC)"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - architektur
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[Model_View_Controller_(MVC)]]

- **Kernkonzept:** Das [[Model_View_Controller_(MVC)|MVC-Muster]] trennt die [[Logik]] einer Anwendung in drei [[Komponente|Komponenten]]: [[Modell]] (Daten und Geschäftslogik), [[View]] (Darstellung) und [[Controller]] (Steuerung). Dies fördert die [[Wiederverwendbarkeit]] und [[Modularität]] von [[Code]].
- **Nutzen & Zweck:** Es löst das [[Problem]] der [[Vermischung]] von [[Darstellung]] und [[Logik]], indem es klare [[Schnittstellen]] zwischen den [[Komponente|Komponenten]] schafft. Dadurch wird die [[Wartbarkeit]] und [[Erweiterbarkeit]] von [[Software]] verbessert.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache Anwendungen, bei denen der [[Overhead]] der Trennung nicht gerechtfertigt ist. Alternativen wie [[Model_View_Presenter_(MVP)]] oder [[Model_View_ViewModel_(MVVM)]] können in bestimmten [[Kontext|Kontexten]] besser passen, z. B. bei stark [[Event-gesteuertes_System|Event-gesteuerten Systemen]].
- **Beispiel / Code:** ```java
// Beispiel für eine einfache MVC-Implementierung
public class StateMachineImpl implements StateMachine, Subject {
    private List<Observer> observers = new ArrayList<>();
    private State currentState;
    
    public void attach(Observer obs) {
        this.observers.add(obs);
        obs.update(currentState);
    }
    
    public void setState(State state) {
        currentState = state;
        observers.forEach(obs -> obs.update(state));
    }
}
```
