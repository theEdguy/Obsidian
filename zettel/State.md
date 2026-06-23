---
id: 697b776c-4120-44ac-bdea-8fa024a51f0a
title: "State"
date: 2026-06-23
tags:
  - software_engineering
  - state
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[State]]

- **Kernkonzept:** Das State-Design-Pattern ist ein Verhaltensmuster, das es einem Objekt ermöglicht, sein Verhalten zu ändern, wenn sich sein interner Zustand ändert. Das Objekt scheint dabei seine Klasse zu wechseln, indem es die Zustandslogik in separate Klassen auslagert.
- **Nutzen & Zweck:** Das State-Pattern löst das Problem, komplexe Bedingungslogik (z. B. viele if-else- oder switch-case-Anweisungen) in einem Objekt zu vermeiden, die dessen Zustand und Verhalten steuert. Es fördert die Wartbarkeit und Erweiterbarkeit, indem Zustände als eigenständige Klassen gekapselt werden. Dadurch wird der Code übersichtlicher, und neue Zustände lassen sich einfacher hinzufügen, ohne bestehende Logik zu verändern.
- **Abgrenzung & Grenzen:** Das State-Pattern sollte nicht genutzt werden, wenn ein Objekt nur wenige oder einfache Zustände besitzt, da der Overhead durch zusätzliche Klassen die Komplexität unnötig erhöht. Es unterscheidet sich von einfachen Zustandsvariablen durch die strikte Trennung der Zustandslogik in eigene Klassen. Alternativen wie Strategie-Pattern oder einfache Zustandsvariablen können sinnvoller sein, wenn die Zustandsübergänge trivial sind oder keine dynamische Verhaltensänderung erforderlich ist.
- **Beispiel / Code:** ```java
// Kontext-Klasse, die den Zustand hält
public class Context {
    private State state;
    
    public Context() {
        state = new ConcreteStateA();
    }
    
    public void setState(State state) {
        this.state = state;
    }
    
    public void request() {
        state.handle(this);
    }
}

// Zustands-Interface
public interface State {
    void handle(Context context);
}

// Konkrete Zustände
public class ConcreteStateA implements State {
    public void handle(Context context) {
        System.out.println("Verhalten im Zustand A");
        context.setState(new ConcreteStateB());
    }
}

public class ConcreteStateB implements State {
    public void handle(Context context) {
        System.out.println("Verhalten im Zustand B");
        context.setState(new ConcreteStateA());
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7c4
- **Vorgänger / Parent:** [[Verhaltensmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Verhaltensmuster]]
  - [[Design_Pattern]]
