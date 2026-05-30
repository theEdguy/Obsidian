---
id: 7fcd6163-c51f-4f54-a2e2-e972bb3de2c3
title: "Model_View_Controller_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - architekturmuster
  - software_architektur
  - draft
source: "SWE Slides (Folien 226-240)"
---

# [[Model_View_Controller_Pattern]]

- **Kernkonzept:** Das [[Model_View_Controller_Pattern|MVC-Muster]] trennt eine interaktive [[Anwendung]] in drei [[Komponente|Komponenten]]: [[Modell]] (Daten und domänenspezifische [[Logik]]), [[View]] (Darstellung) und [[Controller]] (Eingabe-Verarbeitung). Dies fördert die [[Trennung_von_Zuständigkeiten|Trennung von Zuständigkeiten]].
- **Nutzen & Zweck:** Es löst das Problem der [[Vermischung_von_Zuständigkeiten|Vermischung von Zuständigkeiten]] in [[Benutzeroberfläche|Benutzeroberflächen]] und ermöglicht [[Wiederverwendbarkeit]], [[Erweiterbarkeit]] sowie [[Wartbarkeit]] durch klare [[Schnittstelle|Schnittstellen]] zwischen den [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]] mit minimaler [[Logik]] oder wenn die [[Trennung_von_Zuständigkeiten]] unnötigen Overhead verursacht. Unterscheidet sich von [[MVVM_Pattern]] durch die direkte Abhängigkeit der [[View]] vom [[Modell]] und [[Controller]].
- **Beispiel / Code:** ```java
// Modell
public class UserModel {
    private String name;
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
}

// View
public class UserView {
    public void displayUserName(String name) {
        System.out.println("User: " + name);
    }
}

// Controller
public class UserController {
    private UserModel model;
    private UserView view;
    
    public UserController(UserModel model, UserView view) {
        this.model = model;
        this.view = view;
    }
    
    public void updateUserName(String name) {
        model.setName(name);
        view.displayUserName(model.getName());
    }
}
```
