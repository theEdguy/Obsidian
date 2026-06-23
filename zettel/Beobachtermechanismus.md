---
id: 983ec31b-8cf9-45f8-a190-bad5d405f5c8
title: "Beobachtermechanismus"
date: 2026-06-23
tags:
  - software_engineering
  - mechanism
  - communication
  - draft
source: "software_engineering_kapitel_11"
---

# [[Beobachtermechanismus]]

- **Kernkonzept:** Der Beobachtermechanismus ist ein Entwurfsmuster, das eine indirekte Kommunikation zwischen Objekten ermöglicht, indem ein Subjekt (Observable) Änderungen seines Zustands an registrierte Beobachter (Observer) automatisch weiterleitet, ohne dass diese direkt voneinander abhängen.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der engen Kopplung zwischen Komponenten, die voneinander abhängig sind, aber unabhängig voneinander aktualisiert werden sollen. Es ermöglicht eine lose Kopplung, indem es die Benachrichtigung über Zustandsänderungen automatisiert und so die Wartbarkeit, Erweiterbarkeit und Modularität von Software verbessert. Besonders nützlich ist es in interaktiven Anwendungen wie GUIs, wo sich Daten häufig ändern und mehrere Ansichten synchronisiert werden müssen.
- **Abgrenzung & Grenzen:** Der Beobachtermechanismus sollte nicht eingesetzt werden, wenn die Kommunikation zwischen Objekten einfach und direkt erfolgen kann oder wenn die Anzahl der Beobachter sehr groß ist, da dies zu Performance-Problemen führen kann. Alternativen wie direkte Methodenaufrufe oder Event-Busse sind vorzuziehen, wenn die Komplexität der indirekten Kommunikation nicht benötigt wird. Zudem ist das Muster ungeeignet, wenn die Reihenfolge der Benachrichtigungen kritisch ist, da diese nicht garantiert werden kann.
- **Beispiel / Code:** ```java
// Subjekt (Observable)
public interface Subject {
    void registerObserver(Observer o);
    void removeObserver(Observer o);
    void notifyObservers();
}

// Beobachter (Observer)
public interface Observer {
    void update(String message);
}

// Konkrete Implementierung des Subjekts
public class NewsAgency implements Subject {
    private List<Observer> observers = new ArrayList<>();
    private String news;

    @Override
    public void registerObserver(Observer o) {
        observers.add(o);
    }

    @Override
    public void removeObserver(Observer o) {
        observers.remove(o);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(news);
        }
    }

    public void setNews(String news) {
        this.news = news;
        notifyObservers();
    }
}

// Konkrete Implementierung des Beobachters
public class NewsChannel implements Observer {
    private String news;

    @Override
    public void update(String news) {
        this.news = news;
        System.out.println("NewsChannel received: " + news);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1
- **Vorgänger / Parent:** [[Observer-Pattern]]
- **Folgezettel / Unterzettel:**
  - [[Anmeldung]]
  - [[Abmeldung]]
  - [[Benachrichtigungslogik]]
- **Querverweise:**
  - [[Event-Handling]]
  - [[Callback-Mechanismen]]
