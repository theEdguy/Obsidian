---
id: b6c3d1fa-af47-45c2-a90f-205997059820
title: "Model-View-Controller"
date: 2026-06-23
tags:
  - software_engineering
  - architekturmuster
  - design_pattern
  - mvc
  - architektur
  - software_architecture
  - ui
  - draft
source: "software_engineering_kapitel_11"
---

# [[Model-View-Controller]]

- **Kernkonzept:** [[Model-View-Controller]] (MVC) ist ein [[Architekturmuster]], das eine [[Anwendung]] in drei klar getrennte [[Komponente|Komponenten]] unterteilt: Das [[Model]] verwaltet [[Daten]] und [[Geschäftslogik]], die [[View]] ist für die [[Darstellung]] und [[Benutzerinteraktion]] zuständig, und der [[Controller]] steuert den [[Datenfluss]] zwischen [[Model]] und [[View]] sowie die Verarbeitung von [[Benutzereingabe|Benutzereingaben]]. Es fördert die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] und verbessert [[Modularität]], [[Wiederverwendbarkeit]] sowie [[Testbarkeit]].
- **Nutzen & Zweck:** MVC existiert, um die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] in [[Softwareanwendung|Softwareanwendungen]] zu fördern und die [[Wartbarkeit]], [[Erweiterbarkeit]] sowie [[Testbarkeit]] zu verbessern. Es löst das Problem der Vermischung von [[Präsentationslogik]], [[Geschäftslogik]] und [[Datenhaltung]], indem es klare [[Schnittstelle|Schnittstellen]] und [[Verantwortlichkeit|Verantwortlichkeiten]] definiert. Dadurch können [[Entwicklungsteam|Entwicklungsteams]] parallel an verschiedenen [[Schicht|Schichten]] arbeiten, ohne sich gegenseitig zu blockieren, und [[Änderung|Änderungen]] in einer [[Komponente]] haben minimale Auswirkungen auf die anderen. Besonders nützlich ist MVC für [[Webanwendung|Webanwendungen]] und [[GUI|GUIs]], da es die [[Modularität]] und [[Wiederverwendbarkeit]] von [[Code]] erhöht. Durch die klare Aufteilung wird unübersichtlicher und schwer wartbarer [[Code]] vermieden, der bei wachsender [[Komplexität]] von [[Anwendung|Anwendungen]] entsteht. MVC ermöglicht zudem eine bessere [[Kollaboration]] in [[Projekt|Projekten]], da [[Frontend]]- und [[Backend]]-Entwickler unabhängig voneinander arbeiten können.
- **Abgrenzung & Grenzen:** MVC sollte nicht genutzt werden, wenn die [[Anwendung]] sehr einfach ist und keine komplexe [[Benutzerschnittstelle]] oder [[Geschäftslogik]] erfordert, da der Overhead der [[Trennung_von_Zuständigkeiten|Trennung]] die Vorteile überwiegen kann. Es eignet sich weniger für [[Echtzeitsystem|Echtzeitsysteme]] mit hohen [[Performance]]-Anforderungen, da die [[Kommunikation]] zwischen den [[Komponente|Komponenten]] zusätzliche [[Latenz]] verursachen kann. Alternativen wie [[Model-View-ViewModel]] (MVVM) oder [[Model-View-Presenter]] (MVP) sind besser geeignet, wenn eine stärkere [[Entkopplung]] der [[View]] oder eine einfachere [[Testbarkeit]] der [[Präsentationslogik]] im Vordergrund steht. MVVM eignet sich besonders für datengetriebene [[Anwendung|Anwendungen]] mit [[Datenbindung|bidirektionaler Datenbindung]], während MVP eine strengere [[Trennung_von_Zuständigkeiten|Trennung]] zwischen [[View]] und [[Presenter]] vorsieht. MVC ist zudem weniger geeignet für [[System|Systeme]], die eine direkte [[Kopplung]] zwischen [[Komponente|Komponenten]] erfordern, wie z. B. in [[Echtzeitanwendung|Echtzeitanwendungen]] oder [[Spieleentwicklung|Spielen]].
- **Beispiel / Code:** ```java
// Beispiel für eine erweiterte MVC-Struktur in Java mit Benutzerinteraktion und Observer-Pattern

// Model: Verwaltet Daten und Geschäftslogik (Subjekt im Observer-Pattern)
public class UserModel {
    private String name;
    private List<Observer> observers = new ArrayList<>();

    public void addObserver(Observer observer) {
        observers.add(observer);
    }

    public void removeObserver(Observer observer) {
        observers.remove(observer);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
        notifyObservers();
    }

    private void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(name);
        }
    }
}

// Observer-Interface für die View
public interface Observer {
    void update(String data);
}

// View: Stellt Daten dar und nimmt Benutzereingaben entgegen (Beobachter im Observer-Pattern)
public class UserView implements Observer {
    @Override
    public void update(String name) {
        System.out.println("Benutzername aktualisiert: " + name);
    }

    public String getUserInput() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Geben Sie einen Namen ein: ");
        return scanner.nextLine();
    }
}

// Controller: Steuert den Datenfluss zwischen Model und View
public class UserController {
    private UserModel model;
    private UserView view;

    public UserController(UserModel model, UserView view) {
        this.model = model;
        this.view = view;
        model.addObserver(view);
    }

    public void updateUserName() {
        String name = view.getUserInput();
        model.setName(name);
    }
}

// Beispiel für die Nutzung des MVC-Musters mit Observer-Pattern
public class MVCDemo {
    public static void main(String[] args) {
        UserModel model = new UserModel();
        UserView view = new UserView();
        UserController controller = new UserController(model, view);
        
        controller.updateUserName();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Observer-Pattern]]
  - [[Indirekte_Kommunikation]]
  - [[MVC-Implementierung]]
  - [[MVC-Strukturen]]
- **Querverweise:**
  - [[Design_Pattern]]
  - [[Software-Architektur]]
  - [[Benutzeroberfläche]]
