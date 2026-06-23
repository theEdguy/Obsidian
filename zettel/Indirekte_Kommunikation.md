---
id: 96696134-447c-4cf1-888d-335135caf985
title: "Indirekte Kommunikation"
date: 2026-06-23
tags:
  - software_engineering
  - communication
  - design_principle
  - draft
source: "software_engineering_kapitel_11"
---

# [[Indirekte Kommunikation]]

- **Kernkonzept:** Indirekte Kommunikation ist ein Designprinzip, bei dem Komponenten nicht direkt miteinander interagieren, sondern über eine vermittelnde Instanz (z. B. ein Observer-Pattern) Informationen austauschen. Dies trennt Abhängigkeiten und ermöglicht flexible, entkoppelte Systeme.
- **Nutzen & Zweck:** Das Konzept löst das Problem enger Kopplung zwischen Komponenten, die zu schwer wartbaren und unflexiblen Systemen führt. Durch indirekte Kommunikation können Änderungen an einer Komponente vorgenommen werden, ohne andere Komponenten direkt zu beeinflussen. Es fördert Wiederverwendbarkeit, Testbarkeit und Skalierbarkeit, insbesondere in interaktiven Anwendungen wie dem Model-View-Controller (MVC)-Pattern.
- **Abgrenzung & Grenzen:** Indirekte Kommunikation sollte nicht eingesetzt werden, wenn direkte Interaktionen zwischen Komponenten einfacher und performanter sind, z. B. in kleinen, statischen Systemen ohne Änderungsanforderungen. Alternativen wie direkte Methodenaufrufe oder Event-Busse können in solchen Fällen effizienter sein. Zudem erhöht indirekte Kommunikation die Komplexität durch zusätzliche Abstraktionsschichten, was in Echtzeit-Systemen mit strengen Latenzanforderungen problematisch sein kann.
- **Beispiel / Code:** ```java
// Observer-Interface
public interface Observer {
    void update(String message);
}

// Subjekt (Observable)
public class Subject {
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void notifyObservers(String message) {
        for (Observer observer : observers) {
            observer.update(message);
        }
    }
}

// Beispiel-Observer
public class ConcreteObserver implements Observer {
    @Override
    public void update(String message) {
        System.out.println("Empfangen: " + message);
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        Subject subject = new Subject();
        Observer observer = new ConcreteObserver();
        subject.addObserver(observer);
        subject.notifyObservers("Hallo, indirekte Kommunikation!");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Model-View-Controller]]
- **Folgezettel / Unterzettel:**
  - [[Benachrichtigungsmechanismus]]
  - [[Propagierung_von_Benutzereingaben]]
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[Mediator-Pattern]]
