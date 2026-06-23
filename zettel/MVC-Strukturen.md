---
id: dc0b2c68-28c9-418b-9e8b-396fb6220933
title: "MVC-Strukturen"
date: 2026-06-23
tags:
  - software_engineering
  - architecture
  - design
  - draft
source: "software_engineering_kapitel_11"
---

# [[MVC-Strukturen]]

- **Kernkonzept:** MVC-Strukturen (Model-View-Controller) sind ein architektonisches Entwurfsmuster, das eine interaktive Anwendung in drei klar getrennte Komponenten unterteilt: Das Modell verwaltet die Daten und Geschäftslogik, die View stellt die Benutzeroberfläche dar, und der Controller verarbeitet Benutzereingaben und steuert die Interaktion zwischen Modell und View.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Komplexität von Softwareanwendungen zu reduzieren, indem es eine klare Trennung der Verantwortlichkeiten ermöglicht. Es löst das Problem der Vermischung von Präsentation, Logik und Datenhaltung, was die Wartbarkeit, Erweiterbarkeit und Testbarkeit von Anwendungen deutlich verbessert. Zudem ermöglicht es die parallele Entwicklung von Benutzeroberfläche und Geschäftslogik sowie die Wiederverwendung von Modellen oder Views in verschiedenen Kontexten.
- **Abgrenzung & Grenzen:** MVC sollte nicht genutzt werden, wenn die Anwendung sehr einfach ist und keine komplexe Benutzeroberfläche oder Geschäftslogik erfordert, da der Overhead der Trennung die Entwicklung unnötig verkomplizieren kann. Alternativen wie MVVM (Model-View-ViewModel) eignen sich besser für datengetriebene Anwendungen mit bidirektionaler Datenbindung, während MVP (Model-View-Presenter) oft in Anwendungen mit starker Testautomatisierung bevorzugt wird. MVC ist zudem weniger geeignet für Echtzeitanwendungen, bei denen eine direkte Kommunikation zwischen Komponenten erforderlich ist.
- **Beispiel / Code:** ```java
// Beispiel: Einfache MVC-Implementierung in Java

// Modell
class MitgliedModel {
    private String name;
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
        notifyObservers();
    }
    
    private List<Observer> observers = new ArrayList<>();
    
    public void addObserver(Observer observer) {
        observers.add(observer);
    }
    
    private void notifyObservers() {
        for (Observer observer : observers) {
            observer.update();
        }
    }
}

// View
class MitgliedView implements Observer {
    public void display(String name) {
        System.out.println("Mitgliedsname: " + name);
    }
    
    @Override
    public void update() {
        // Aktualisierung der Anzeige
    }
}

// Controller
class MitgliedController {
    private MitgliedModel model;
    private MitgliedView view;
    
    public MitgliedController(MitgliedModel model, MitgliedView view) {
        this.model = model;
        this.view = view;
        model.addObserver(view);
    }
    
    public void setMitgliedsname(String name) {
        model.setName(name);
    }
    
    public String getMitgliedsname() {
        return model.getName();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Model-View-Controller]]
- **Folgezettel / Unterzettel:**
  - [[Komponentenzerlegung]]
  - [[Use-Case-Komponenten]]
- **Querverweise:**
  - [[Domain-Driven_Design]]
  - [[Komponentenbasierte_Architektur]]
