---
id: fce12c99-ede3-4ae3-9830-1604421a0250
title: "Observer"
date: 2026-06-23
tags:
  - software_engineering
  - observer
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Observer]]

- **Kernkonzept:** Das Observer-Muster ist ein Entwurfsmuster, bei dem ein Objekt (Subject) eine Liste von abhängigen Objekten (Observers) verwaltet und diese automatisch über Zustandsänderungen informiert, ohne eine enge Kopplung zwischen ihnen zu erzeugen.
- **Nutzen & Zweck:** Das Observer-Muster löst das Problem der dynamischen Benachrichtigung mehrerer Komponenten über Änderungen in einem zentralen Objekt. Es ermöglicht eine lose Kopplung zwischen dem Subject und seinen Observers, sodass neue Observer hinzugefügt oder entfernt werden können, ohne das Subject zu modifizieren. Dies fördert die Wartbarkeit und Erweiterbarkeit von Software, insbesondere in Systemen mit verteilten oder asynchronen Ereignissen, wie z. B. Benutzeroberflächen oder Event-gesteuerten Architekturen.
- **Abgrenzung & Grenzen:** Das Observer-Muster sollte nicht verwendet werden, wenn die Anzahl der Observer sehr groß ist oder häufige Änderungen am Subject auftreten, da dies zu Performance-Problemen führen kann. Es eignet sich auch nicht für Szenarien, in denen eine strikte Kontrolle über die Reihenfolge der Benachrichtigungen erforderlich ist. Alternativen wie das Mediator-Muster oder direkte Callback-Mechanismen können in solchen Fällen besser geeignet sein. Zudem ist das Muster weniger sinnvoll, wenn nur ein einziger Observer existiert oder die Beziehung zwischen Subject und Observer statisch ist.
- **Beispiel / Code:** ```java
import java.util.ArrayList;
import java.util.List;

// Subject (Observable)
interface Subject {
    void attach(Observer observer);
    void detach(Observer observer);
    void notifyObservers();
}

// Concrete Subject
class Wetterstation implements Subject {
    private int temperatur;
    private List<Observer> observers = new ArrayList<>();

    public void setTemperatur(int temperatur) {
        this.temperatur = temperatur;
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
            observer.update(temperatur);
        }
    }
}

// Observer
interface Observer {
    void update(int temperatur);
}

// Concrete Observer
class Display implements Observer {
    @Override
    public void update(int temperatur) {
        System.out.println("Aktuelle Temperatur: " + temperatur + "°C");
    }
}

// Verwendung
public class ObserverPatternDemo {
    public static void main(String[] args) {
        Wetterstation wetterstation = new Wetterstation();
        Display display = new Display();
        wetterstation.attach(display);
        wetterstation.setTemperatur(25);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7c1
- **Vorgänger / Parent:** [[Verhaltensmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Verhaltensmuster]]
  - [[Design_Pattern]]
