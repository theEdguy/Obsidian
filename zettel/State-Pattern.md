---
id: 15364217-ae85-4c71-8a96-2d15b73e19f5
title: "State-Pattern"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - zustand
  - verhalten
  - draft
source: "software_engineering_kapitel_12"
---

# [[State-Pattern]]

- **Kernkonzept:** Das State-Pattern ist ein Verhaltensmuster, das es einem Objekt ermöglicht, sein Verhalten zu ändern, wenn sich sein interner Zustand ändert. Dabei wird der Zustand in separate Klassen ausgelagert, die das Verhalten für den jeweiligen Zustand kapseln.
- **Nutzen & Zweck:** Das State-Pattern löst das Problem, komplexe bedingte Logik (z. B. if-else- oder switch-case-Anweisungen) in einem Objekt zu vermeiden, indem Zustände und deren Übergänge explizit modelliert werden. Es verbessert die Wartbarkeit und Erweiterbarkeit, da neue Zustände einfach hinzugefügt werden können, ohne bestehende Logik zu verändern. Zudem macht es den Code übersichtlicher, indem es Zustandsübergänge und -verhalten klar strukturiert.
- **Abgrenzung & Grenzen:** Das State-Pattern sollte nicht genutzt werden, wenn ein Objekt nur wenige Zustände mit einfacher Logik besitzt, da der Overhead durch zusätzliche Klassen den Nutzen übersteigt. Es unterscheidet sich von einfachen Zustandsvariablen (z. B. Enums) durch die Kapselung von Verhalten in separaten Klassen, was bei komplexen Zustandsübergängen sinnvoll ist. Alternativen wie Strategie-Pattern eignen sich besser, wenn Algorithmen unabhängig vom Zustand ausgetauscht werden sollen, ohne den Kontext zu verändern.
- **Beispiel / Code:** ```java
public interface State {
    void handle(Context context);
}

public class ConcreteStateA implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Zustand A: Verhalten für Zustand A");
        context.setState(new ConcreteStateB());
    }
}

public class Context {
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
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Observer-Pattern]]
- **Folgezettel / Unterzettel:**
  - [[Zustandsverwaltung]]
  - [[State-Interface]]
  - [[Zustandsübergänge]]
- **Querverweise:**
  - [[Design_Patterns]]
  - [[Protokoll-Automaten]]
