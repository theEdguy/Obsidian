---
id: 56705c38-9505-4cb4-8875-e2ab5cd19193
title: "Update-Methode"
date: 2026-06-23
tags:
  - software_engineering
  - beobachtung
  - methode
  - mvc
  - draft
source: "software_engineering_kapitel_12"
---

# [[Update-Methode]]

- **Kernkonzept:** Die Update-Methode ist eine zentrale Komponente im Observer-Muster des Model-View-Controller (MVC)-Paradigmas, die dafür sorgt, dass Beobachter (Observer) über Zustandsänderungen des Subjekts informiert werden und ihre Darstellung entsprechend anpassen.
- **Nutzen & Zweck:** Die Update-Methode löst das Problem der losen Kopplung zwischen Datenmodell (Model) und Benutzeroberfläche (View). Sie ermöglicht es, dass mehrere Views oder Controller automatisch und effizient über Änderungen im Subjekt benachrichtigt werden, ohne dass das Subjekt direkte Kenntnis seiner Beobachter haben muss. Dies fördert die Wartbarkeit und Erweiterbarkeit von Software, da neue Beobachter hinzugefügt werden können, ohne das Subjekt zu modifizieren.
- **Abgrenzung & Grenzen:** Die Update-Methode sollte nicht eingesetzt werden, wenn eine direkte und enge Kopplung zwischen Komponenten erforderlich ist, beispielsweise bei Performance-kritischen Systemen, in denen der Overhead der Benachrichtigungsmechanismen nicht tolerierbar ist. Alternativen wie Polling oder direkte Methodenaufrufe können in solchen Fällen sinnvoller sein. Zudem ist das Observer-Muster weniger geeignet, wenn die Zustandsänderungen extrem häufig oder komplex sind, da dies zu unnötigen Aktualisierungen und Performance-Einbußen führen kann.
- **Beispiel / Code:** ```java
public interface Observer {
    void update(State newState);
}

public class StateMachineImpl implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private State currentState;

    public void attach(Observer obs) {
        observers.add(obs);
        obs.update(currentState);
    }

    public void setState(State state) {
        currentState = state;
        observers.forEach(obs -> obs.update(state));
    }
}

public class View implements Observer {
    @Override
    public void update(State newState) {
        System.out.println("View aktualisiert: Neuer Zustand ist " + newState);
        // Logik zur Anpassung der Darstellung
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1a
- **Vorgänger / Parent:** [[Observer-Interface]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[Benachrichtigungsmechanismus]]
