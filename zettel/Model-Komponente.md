---
id: 6399cc5e-f0a2-4055-a011-ac41218f2caf
title: "Model-Komponente"
date: 2026-06-23
tags:
  - software_engineering
  - mvc
  - modell
  - zustand
  - draft
source: "software_engineering_kapitel_12"
---

# [[Model-Komponente]]

- **Kernkonzept:** Die Model-Komponente im MVC-Muster (Model-View-Controller) repräsentiert die zentrale Daten- und Geschäftslogik einer Anwendung sowie deren Zustand. Sie kapselt die Datenstruktur, Validierungsregeln und die Geschäftsprozesse, die für die Funktionalität des Systems essenziell sind, und stellt diese anderen Komponenten zur Verfügung, ohne deren Implementierungsdetails preiszugeben.
- **Nutzen & Zweck:** Die Model-Komponente existiert, um eine klare Trennung zwischen der Darstellung der Daten (View) und der Steuerungslogik (Controller) zu ermöglichen. Dies löst das Problem der Vermischung von Verantwortlichkeiten, verbessert die Wartbarkeit und ermöglicht die Wiederverwendung der Geschäftslogik in verschiedenen Kontexten. Zudem erlaubt sie eine konsistente Zustandsverwaltung, da alle Änderungen am Systemzustand zentral im Model erfolgen und über definierte Schnittstellen kommuniziert werden.
- **Abgrenzung & Grenzen:** Die Model-Komponente sollte nicht genutzt werden, wenn die Anwendung keine komplexe Geschäftslogik oder Zustandsverwaltung erfordert, da der Overhead der Trennung in solchen Fällen unnötig ist. Alternativen wie ein reines Datenzugriffsobjekt (DAO) oder einfache Datencontainer können in trivialen Anwendungen ausreichen. Im Gegensatz zu Views oder Controllern, die direkt mit Benutzereingaben oder der Darstellung interagieren, sollte das Model keine Annahmen über die Präsentation oder Steuerung treffen, um seine Unabhängigkeit zu wahren.
- **Beispiel / Code:** ```java
public class MemberModel implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String memberName;
    private State currentState;

    public void setMemberName(String name) {
        this.memberName = name;
        notifyObservers();
    }

    public String getMemberName() {
        return memberName;
    }

    public State getCurrentState() {
        return currentState;
    }

    public void setCurrentState(State state) {
        this.currentState = state;
        notifyObservers();
    }

    @Override
    public void attach(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void detach(Observer observer) {
        observers.remove(observer);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(this);
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[MVC-Architektur]]
- **Folgezettel / Unterzettel:**
  - [[State-Pattern]]
  - [[Zustandsverwaltung]]
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[MVC-Architektur]]
