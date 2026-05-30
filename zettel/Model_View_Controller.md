---
id: 5e971ce9-fc68-459e-96c0-3c404589ce8f
title: "Model_View_Controller"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - uml
  - separation_of_concerns
  - observer_pattern
  - draft
source: "Klausur_Referenz"
---

# [[Model_View_Controller]]

- **Kernkonzept:** Das **Model_View_Controller** (MVC) ist ein [[Architekturmuster]], das die Struktur interaktiver Anwendungen in drei zentrale Komponenten unterteilt: 
- **Model**: Enthält die Geschäftslogik und Daten (z. B. `coreData`). Es kapselt den Zustand der Anwendung und stellt Methoden wie `getData()` bereit, um diesen Zustand abzufragen oder zu modifizieren. Das Model ist unabhängig von der Darstellung und Benutzerinteraktion.
- **View**: Verantwortlich für die Darstellung der Daten (z. B. `viewState`). Sie beobachtet das [[Model]] (oft über das [[Observer_Pattern]]) und aktualisiert sich bei Änderungen, ohne die Daten selbst zu verändern. Typische Methoden sind `display()`.
- **Controller**: Verarbeitet Benutzereingaben (z. B. `handleEvent()`) und übersetzt sie in Aktionen auf dem [[Model]] oder der [[View]]. Er fungiert als Vermittler zwischen beiden Komponenten und enthält oft `controllerState` zur Steuerung des Ablaufs.

Die Trennung dieser Verantwortlichkeiten fördert die [[Wartbarkeit]] und [[Erweiterbarkeit]] von Software.
- **Nutzen & Zweck:** MVC wird eingesetzt, um:
- **Trennung von Belangen** ([[Separation_of_Concerns]]) zu erreichen: Jede Komponente hat eine klare Aufgabe, was die Komplexität reduziert.
- **Wiederverwendbarkeit** zu erhöhen: Views oder Controller können ausgetauscht werden, ohne das Model zu ändern (z. B. verschiedene Oberflächen für dieselbe Logik).
- **Parallelentwicklung** zu ermöglichen: Teams können unabhängig an Model, View oder Controller arbeiten.
- **Testbarkeit** zu verbessern: Komponenten lassen sich isoliert testen (z. B. Unit-Tests für das Model).

Typische Anwendungsfälle sind Webanwendungen (z. B. [[Ruby_on_Rails]]), Desktop-Software (z. B. [[Java_Swing]]) oder mobile Apps.
- **Abgrenzung & Grenzen:** 1. **Missverständnisse**: 
   - *View ≠ UI*: Die View ist nicht nur die grafische Oberfläche, sondern jede Darstellung der Daten (z. B. auch JSON-Ausgabe).
   - *Model ≠ Datenbank*: Das Model enthält Geschäftslogik, nicht nur Rohdaten. Eine Datenbank ist lediglich ein [[Persistence_Layer]].
   - *Controller ≠ Business-Logik*: Der Controller koordiniert, führt aber keine komplexe Logik aus (diese gehört ins Model).

2. **Grenzen**:
   - **Zyklische Abhängigkeiten**: Bei falscher Implementierung kann es zu engen Kopplungen kommen (z. B. wenn der Controller direkt die View manipuliert).
   - **Überkomplexität**: Für einfache Anwendungen kann MVC zu viel Aufwand bedeuten.
   - **Variationen**: Es gibt Abwandlungen wie [[Model_View_Presenter]] (MVP) oder [[Model_View_ViewModel]] (MVVM), die andere Schwerpunkte setzen.

3. **Stolpersteine**:
   - *Fat Controller*: Wenn der Controller zu viel Logik übernimmt, verletzt dies das Prinzip der [[Single_Responsibility_Principle]].
   - *Direkte Kommunikation*: Views sollten nicht direkt auf das Model zugreifen, sondern über den Controller oder Observer-Mechanismen.
   - *Zustandsmanagement*: Bei vielen Views/Controllern kann die Synchronisation des Models herausfordernd sein.
- **Beispiel / Code:** {'beschreibung': 'UML-Klassendiagramm (textuell) zur Veranschaulichung der MVC-Struktur:', 'uml': '```mermaid\nclassDiagram\n    class Model {\n        +coreData: Data\n        +getData() Data\n        +updateData(newData: Data)\n    }\n    \n    class View {\n        +viewState: State\n        +display(data: Data)\n        +update()\n    }\n    \n    class Controller {\n        +controllerState: State\n        +handleEvent(event: Input)\n    }\n    \n    Model "1" --* "1..*" View : observes\n    Controller "1" --> "1" Model : manipulates\n    Controller "1" --> "1..*" View : updates\n    View ..> Model : requests data\n```', 'code_beispiel': {'sprache': 'Java', 'beschreibung': 'Vereinfachtes Beispiel für eine MVC-Implementierung mit Observer-Pattern:', 'code': '// Model\npublic class UserModel {\n    private String name;\n    private List<Observer> observers = new ArrayList<>();\n    \n    public void setName(String name) {\n        this.name = name;\n        notifyObservers();\n    }\n    \n    public String getName() {\n        return name;\n    }\n    \n    public void addObserver(Observer observer) {\n        observers.add(observer);\n    }\n    \n    private void notifyObservers() {\n        for (Observer observer : observers) {\n            observer.update();\n        }\n    }\n}\n\n// View (Observer)\npublic class UserView implements Observer {\n    private UserModel model;\n    \n    public UserView(UserModel model) {\n        this.model = model;\n        model.addObserver(this);\n    }\n    \n    public void display() {\n        System.out.println("Name: " + model.getName());\n    }\n    \n    @Override\n    public void update() {\n        display();\n    }\n}\n\n// Controller\npublic class UserController {\n    private UserModel model;\n    private UserView view;\n    \n    public UserController(UserModel model, UserView view) {\n        this.model = model;\n        this.view = view;\n    }\n    \n    public void setUserName(String name) {\n        model.setName(name);\n    }\n}\n\n// Anwendung\npublic class Main {\n    public static void main(String[] args) {\n        UserModel model = new UserModel();\n        UserView view = new UserView(model);\n        UserController controller = new UserController(model, view);\n        \n        controller.setUserName("Max Mustermann");\n    }\n}'}}
