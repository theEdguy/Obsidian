---
id: 14d61770-2886-49ab-b051-24325b6b400e
title: "Softwareentwurf"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - uml
  - modularitaet
  - design_prinzipien
  - wiederverwendbarkeit
  - technische_dokumentation
  - agile_entwicklung
  - draft
source: "Klausur_Referenz"
---

# [[Softwareentwurf]]

- **Kernkonzept:** Der [[Softwareentwurf]] ist eine zentrale Phase im [[Softwareentwicklungsprozess]], in der die strukturelle und verhaltensbezogene Architektur einer Softwarelösung konzipiert wird. Er umfasst die Definition von [[Schnittstellen]], [[Klassen]], Methoden, Attributen sowie deren Beziehungen und Interaktionen, um funktionale und nicht-funktionale Anforderungen zu erfüllen. Ziel ist es, ein modulares, wartbares und erweiterbares System zu schaffen, das durch klare [[Entwurfsprinzipien]] (z. B. [[SOLID_Prinzipien]]) und [[Entwurfsmuster]] (z. B. [[Observer_Pattern]], [[Singleton_Pattern]]) geprägt ist. Der Entwurf dient als Brücke zwischen der [[Anforderungsanalyse]] und der [[Implementierung]] und wird oft durch [[UML]]-Diagramme (z. B. [[Klassendiagramm]], [[Sequenzdiagramm]]) dokumentiert.
- **Nutzen & Zweck:** Der [[Softwareentwurf]] erfüllt mehrere zentrale Zwecke:

1. **Strukturierung und Modularität**: Durch die Aufteilung des Systems in überschaubare Komponenten (z. B. [[Module]], [[Pakete]]) wird die Komplexität reduziert und die [[Wiederverwendbarkeit]] von Code gefördert.

2. **Qualitätssicherung**: Ein guter Entwurf minimiert Redundanzen, verbessert die [[Kohäsion]] und reduziert die [[Kopplung]], was zu robusterer und fehlerärmerer Software führt. Zudem ermöglicht er die frühzeitige Identifikation von [[Design_Smells]] (z. B. [[God_Object]]).

3. **Dokumentation und Kommunikation**: Der Entwurf dient als Grundlage für die [[Technische_Dokumentation]] und erleichtert die Zusammenarbeit im Team durch ein gemeinsames [[Standardvokabular]] (z. B. [[Domain-Driven_Design]]-Begriffe).

4. **Zukunftssicherheit**: Durch die Anwendung von [[Entwurfsmustern]] und [[Architekturmustern]] (z. B. [[Schichtenarchitektur]], [[Microservices]]) wird die [[Erweiterbarkeit]] und [[Anpassbarkeit]] des Systems an neue Anforderungen sichergestellt.

5. **Effizienzsteigerung**: Automatisierte Werkzeuge (z. B. [[Model-Driven_Development]]) können auf Basis des Entwurfs Code generieren oder [[Refactoring]]-Maßnahmen vorschlagen, was die Entwicklungsgeschwindigkeit erhöht.
- **Abgrenzung & Grenzen:** Der [[Softwareentwurf]] ist abzugrenzen von:

1. **[[Anforderungsanalyse]]**: Während die Analyse *was* das System leisten soll, definiert, legt der Entwurf *wie* dies umgesetzt wird. Eine unklare Trennung führt zu [[Feature_Creep]] oder unnötiger Komplexität.

2. **[[Implementierung]]**: Der Entwurf ist ein *Plan*, nicht der ausführbare Code. Eine zu detaillierte Vorwegnahme von Implementierungsdetails (z. B. konkrete Algorithmen) kann die Flexibilität einschränken.

3. **[[Softwarearchitektur]]**: Die Architektur beschreibt die *grobe Struktur* des Systems (z. B. [[Client-Server_Architektur]]), während der Entwurf die *feingranularen Komponenten* (z. B. Klassen, Methoden) spezifiziert. Eine Vermischung führt zu unklaren Verantwortlichkeiten.

**Typische Stolpersteine**:
- **Über-Engineering**: Zu frühe Festlegung auf komplexe [[Entwurfsmuster]] ohne tatsächlichen Bedarf (z. B. [[Abstract_Factory]] für einfache Anwendungsfälle).
- **Unterschätzung nicht-funktionaler Anforderungen**: Performance, Skalierbarkeit oder Sicherheit werden im Entwurf oft vernachlässigt, was zu kostspieligen Nachbesserungen führt.
- **Fehlende Dokumentation von [[Entwurfsentscheidungen]]**: Ohne Begründung für gewählte Lösungen (z. B. warum [[Dependency_Injection]] statt direkter Instanziierung) wird die Wartbarkeit erschwert.
- **Ignorieren von [[Technischen_Schulden]]**: Kurzfristige Kompromisse (z. B. harte Abhängigkeiten) führen langfristig zu [[Legacy_Code]].
- **Starre Entwurfsprozesse**: Ein zu dogmatisches Festhalten an [[Vorgehensmodellen]] (z. B. reines [[Wasserfallmodell]]) kann iterative Anpassungen blockieren. Moderne Ansätze wie [[Agile_Entwicklung]] erfordern flexible Entwurfsphasen.
- **Beispiel / Code:** {'beschreibung': 'Ein einfaches Beispiel für den Entwurf eines [[Observer_Pattern]] in UML (Mermaid-Syntax) und Java-Code, das die Benachrichtigung von Beobachtern bei Änderungen eines Subjekts zeigt:', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Subject {\n        +attach(Observer o)\n        +detach(Observer o)\n        +notifyObservers()\n    }\n    class Observer {\n        <<interface>>\n        +update()\n    }\n    class ConcreteSubject {\n        -state: String\n        +getState(): String\n        +setState(String state)\n    }\n    class ConcreteObserver {\n        -subject: Subject\n        +update()\n    }\n    Subject <|-- ConcreteSubject\n    Observer <|-- ConcreteObserver\n    Subject "1" *-- "*" Observer : observers\n```', 'java_code': 'public interface Observer {\n    void update();\n}\n\npublic class Subject {\n    private List<Observer> observers = new ArrayList<>();\n    \n    public void attach(Observer o) {\n        observers.add(o);\n    }\n    \n    public void detach(Observer o) {\n        observers.remove(o);\n    }\n    \n    public void notifyObservers() {\n        for (Observer o : observers) {\n            o.update();\n        }\n    }\n}\n\npublic class ConcreteSubject extends Subject {\n    private String state;\n    \n    public String getState() {\n        return state;\n    }\n    \n    public void setState(String state) {\n        this.state = state;\n        notifyObservers(); // Benachrichtigung bei Zustandsänderung\n    }\n}\n\npublic class ConcreteObserver implements Observer {\n    private ConcreteSubject subject;\n    \n    public ConcreteObserver(ConcreteSubject subject) {\n        this.subject = subject;\n        subject.attach(this);\n    }\n    \n    @Override\n    public void update() {\n        System.out.println("Zustand geändert: " + subject.getState());\n    }\n}', 'hinweis': 'Das Beispiel zeigt, wie das [[Observer_Pattern]] die [[Kopplung]] zwischen Subjekt und Beobachtern reduziert und die [[Erweiterbarkeit]] verbessert. Im Entwurf würde dies durch ein [[Klassendiagramm]] dokumentiert.'}
