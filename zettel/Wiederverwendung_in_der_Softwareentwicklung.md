---
aliases:
- Wiederverwendung
date: 2026-05-30
id: 40710d59-cceb-45e0-8a1a-3e32ef8e4f14
source: Klausur_Referenz
tags:
- software_engineering
- entwurfsmuster
- softwarearchitektur
- modularisierung
- designprinzipien
- observer_pattern
- komponentenbasierte_entwicklung
- draft
title: Wiederverwendung_in_der_Softwareentwicklung
---

# [[Wiederverwendung_in_der_Softwareentwicklung]]

- **Kernkonzept:** Wiederverwendung bezeichnet im Software-Engineering die Praxis, bestehende Artefakte wie [[Module]], [[Komponenten]], [[Klassen]], [[Funktionen]], [[Entwurfsmuster]] oder sogar ganze [[Softwarearchitekturen]] in neuen Projekten oder Kontexten erneut einzusetzen, um Entwicklungsaufwand, Kosten und Fehleranfälligkeit zu reduzieren. Ziel ist es, bewährte Lösungen nicht neu zu implementieren, sondern durch gezielte Anpassung oder Komposition nutzbar zu machen. Wiederverwendung kann auf verschiedenen Ebenen erfolgen: von der Code-Ebene (z. B. Bibliotheken) bis hin zu architektonischen Mustern (z. B. [[Microservices]]).
- **Nutzen & Zweck:** Der Hauptzweck der Wiederverwendung liegt in der Steigerung der Effizienz und Qualität in der Softwareentwicklung. Konkrete Vorteile umfassen:
- **Reduzierung von Redundanz**: Vermeidung doppelter Implementierungen gleicher Funktionalität.
- **Schnellere Time-to-Market**: Beschleunigte Entwicklung durch Nutzung vorhandener Bausteine.
- **Erhöhte Wartbarkeit**: Zentrale Pflege wiederverwendeter Komponenten vereinfacht Updates und Fehlerbehebungen.
- **Konsistenz**: Einheitliche Nutzung von [[Schnittstellen]] oder [[Designprinzipien]] (z. B. [[SOLID]]) fördert robuste Systeme.
- **Risikominimierung**: Bewährte Komponenten reduzieren die Wahrscheinlichkeit von Fehlern.

Beispiele für Wiederverwendung sind die Nutzung von Frameworks (z. B. Spring, React), Bibliotheken (z. B. Apache Commons) oder die Anwendung von [[Entwurfsmustern]] wie dem [[Observer_Pattern]] zur Benachrichtigung über Zustandsänderungen – wie im Kontext von 'MyStilberater' angedeutet.
- **Abgrenzung & Grenzen:** Wiederverwendung ist nicht universell einsetzbar und stößt an Grenzen:
- **Überdesign**: Zu frühe oder übermäßige Abstraktion kann zu unnötiger Komplexität führen (vgl. [[YAGNI]]).
- **Abhängigkeiten**: Starke Kopplung an wiederverwendete Komponenten kann Flexibilität einschränken.
- **Anpassungsaufwand**: Nicht alle Komponenten sind ohne Modifikation in neuen Kontexten nutzbar (z. B. bei domänenspezifischen Anforderungen).
- **Versionierung**: Konflikte durch unterschiedliche Versionen wiederverwendeter Artefakte (vgl. [[Dependency_Hell]]).
- **Rechtliche Einschränkungen**: Lizenzbedingungen (z. B. GPL) können die Wiederverwendung einschränken.

Typische Stolpersteine sind:
- **Falsche Granularität**: Zu feingranulare Komponenten erhöhen den Integrationsaufwand, zu grobe Komponenten sind unflexibel.
- **Fehlende Dokumentation**: Schlechte oder veraltete Dokumentation erschwert die Wiederverwendung.
- **Technische Schulden**: Veraltete oder schlecht gewartete Komponenten können neue Projekte belasten.
- **Beispiel / Code:** {'beschreibung': "Das folgende Beispiel veranschaulicht die Wiederverwendung einer [[Observer_Pattern]]-Implementierung in Java, um Nutzer des 'MyStilberater'-Systems über Zustandsänderungen (z. B. neue Stilvorschläge) zu informieren. Die wiederverwendbare Komponente ist das `Subject` (hier: `Stilberater`), das Beobachter (`Observer`) benachrichtigt.", 'code': {'java': {'subject_interface': 'public interface Subject {\n    void registerObserver(Observer observer);\n    void removeObserver(Observer observer);\n    void notifyObservers();\n}', 'observer_interface': 'public interface Observer {\n    void update(String message);\n}', 'stilberater_klasse': 'public class Stilberater implements Subject {\n    private List<Observer> observers = new ArrayList<>();\n    private String latestStyleTip;\n\n    @Override\n    public void registerObserver(Observer observer) {\n        observers.add(observer);\n    }\n\n    @Override\n    public void removeObserver(Observer observer) {\n        observers.remove(observer);\n    }\n\n    @Override\n    public void notifyObservers() {\n        for (Observer observer : observers) {\n            observer.update(latestStyleTip);\n        }\n    }\n\n    public void setLatestStyleTip(String tip) {\n        this.latestStyleTip = tip;\n        notifyObservers();\n    }\n}', 'nutzer_klasse': 'public class Nutzer implements Observer {\n    private String name;\n\n    public Nutzer(String name) {\n        this.name = name;\n    }\n\n    @Override\n    public void update(String message) {\n        System.out.println(name + " erhielt neuen Stil-Tipp: " + message);\n    }\n}', 'anwendung': 'public class Anwendung {\n    public static void main(String[] args) {\n        Stilberater stilberater = new Stilberater();\n        Nutzer nutzer1 = new Nutzer("Max");\n        Nutzer nutzer2 = new Nutzer("Lisa");\n\n        stilberater.registerObserver(nutzer1);\n        stilberater.registerObserver(nutzer2);\n\n        stilberater.setLatestStyleTip("Trage heute Pastellfarben!");\n    }\n}'}}, 'uml_diagramm': {'mermaid': 'classDiagram\n    class Subject {\n        <<interface>>\n        +registerObserver(Observer observer)\n        +removeObserver(Observer observer)\n        +notifyObservers()\n    }\n\n    class Observer {\n        <<interface>>\n        +update(String message)\n    }\n\n    class Stilberater {\n        -List~Observer~ observers\n        -String latestStyleTip\n        +registerObserver(Observer observer)\n        +removeObserver(Observer observer)\n        +notifyObservers()\n        +setLatestStyleTip(String tip)\n    }\n\n    class Nutzer {\n        -String name\n        +update(String message)\n    }\n\n    Subject <|-- Stilberater\n    Observer <|-- Nutzer\n    Stilberater "1" *-- "*" Observer'}}
