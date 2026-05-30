---
id: 8b1fc4e1-67ea-43fd-a8ba-27115a1eda4a
title: "Model-View-Controller"
date: 2026-05-30
tags:
  - software_engineering
  - architekturmuster
  - design_pattern
  - mvc
  - draft
source: "SWE Slides (Folien 211-225)"
---

# [[Model-View-Controller]]

- **Kernkonzept:** [[Model-View-Controller]] (MVC) ist ein [[Architekturmuster]], das eine [[Anwendung]] in drei [[Komponente|Komponenten]] unterteilt: [[Model]] (Daten und Logik), [[View]] (Präsentation) und [[Controller]] (Steuerung der [[Interaktion]]).
- **Nutzen & Zweck:** Es ermöglicht die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]] zwischen [[Benutzerschnittstelle]] und [[Logik]], was die [[Wartbarkeit]] und [[Erweiterbarkeit]] verbessert. Besonders nützlich für [[Webanwendung|Webanwendungen]] und [[GUI|GUIs]].
- **Abgrenzung & Grenzen:** Nicht ideal für [[Echtzeitsystem|Echtzeitsysteme]] mit hoher [[Performance]]-Anforderung, da die Kommunikation zwischen [[Komponente|Komponenten]] [[Latenz]] verursachen kann. Bei einfachen [[Anwendung|Anwendungen]] kann der Overhead unnötig sein.
- **Beispiel / Code:** ```java
// Model
public class UserModel {
    private String name;
    
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}

// View
public class UserView {
    public void displayUser(String name) {
        System.out.println("User: " + name);
    }
}

// Controller
public class UserController {
    private UserModel model;
    private UserView view;
    
    public void updateView() {
        view.displayUser(model.getName());
    }
}
```
