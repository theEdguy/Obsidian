---
id: 7f79e6db-c078-40b0-8eed-82bc38895c1d
title: "Implementierung"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - uml
  - modularisierung
  - agile_entwicklung
  - bridge_pattern
  - draft
source: "Klausur_Referenz"
---

# [[Implementierung]]

- **Kernkonzept:** Die [[Implementierung]] bezeichnet in der Softwareentwicklung die konkrete Umsetzung von [[Schnittstellen]], [[Abstraktionen]] oder Spezifikationen in ausführbaren Code. Sie realisiert die technische Funktionalität, die durch [[Entwurfsmodelle]] (z. B. [[Klassendiagramm]] oder [[Aktivitätsdiagramm]]) vorgegeben ist, und trennt dabei bewusst die äußere [[Schnittstelle]] von internen Details. Dies ermöglicht eine unabhängige Weiterentwicklung beider Ebenen, wie etwa im [[Bridge_Pattern]].
- **Nutzen & Zweck:** 1. **Modularität und Wartbarkeit**: Durch die Trennung von [[Schnittstelle]] und Implementierung können Änderungen an der Implementierung vorgenommen werden, ohne den [[Client]]-Code zu beeinflussen (Prinzip der [[Lose_Kopplung]]).
2. **Wiederverwendbarkeit**: Implementierungen lassen sich in verschiedenen Kontexten einsetzen, z. B. durch [[Dependency_Injection]] oder [[Strategy_Pattern]].
3. **Testbarkeit**: Implementierungen können isoliert getestet werden (z. B. via [[Mocking]] oder [[Unit_Tests]]).
4. **Iterative Entwicklung**: In [[Agile_Entwicklung]] ermöglicht die schrittweise Implementierung von [[Use_Cases]] eine flexible Anpassung an neue Anforderungen.
5. **Architekturklarheit**: Durch [[Packages]] oder Module werden Abhängigkeiten und Verantwortlichkeiten sichtbar (vgl. [[Package_Diagramm]]).
- **Abgrenzung & Grenzen:** - **Nicht gleichzusetzen mit Entwurf**: Die Implementierung folgt dem [[Entwurfsmodell]], ist aber nicht selbst das Modell. Typischer Fehler: Direkte Umsetzung von [[Use_Cases]] in Code ohne vorherige Architekturplanung (vgl. Folie 322).
- **Keine permanente Bindung**: Im Gegensatz zu statischen Vererbungsbeziehungen erlaubt die Implementierung dynamische Austauschbarkeit (z. B. via [[Bridge_Pattern]]).
- **Stolpersteine**: 
  - *Überimplementierung*: Zu frühe Optimierung oder unnötige Komplexität.
  - *Verletzung der [[Schnittstelle]]*: Änderungen an der Implementierung, die die Schnittstelle brechen (vgl. [[Liskovsches_Substitutionsprinzip]]).
  - *Fehlende Abstraktion*: Direkte Abhängigkeit von konkreten Implementierungen statt von [[Schnittstellen]].
- **Grenzen**: Implementierung ist an die Vorgaben des [[Entwurfs]] gebunden; radikale Änderungen erfordern oft eine Neugestaltung der Architektur.
- **Beispiel / Code:** {'beschreibung': 'Beispiel für die Trennung von Abstraktion und Implementierung mittels [[Bridge_Pattern]] (Java-ähnliche Syntax):', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Abstraction {\n        +operation()\n        -Implementor impl\n    }\n    class Implementor {\n        <<interface>>\n        +operationImpl()\n    }\n    class ConcreteImplementorA {\n        +operationImpl()\n    }\n    class ConcreteImplementorB {\n        +operationImpl()\n    }\n    Abstraction --> Implementor\n    Implementor <|-- ConcreteImplementorA\n    Implementor <|-- ConcreteImplementorB\n```', 'code': {'abstraktion': 'public class Abstraction {\n    private Implementor impl;\n\n    public Abstraction(Implementor impl) {\n        this.impl = impl;\n    }\n\n    public void operation() {\n        impl.operationImpl();\n    }\n}', 'implementor': 'public interface Implementor {\n    void operationImpl();\n}', 'konkrete_implementierungen': ['public class ConcreteImplementorA implements Implementor {\n    @Override\n    public void operationImpl() {\n        System.out.println("Implementierung A");\n    }\n}', 'public class ConcreteImplementorB implements Implementor {\n    @Override\n    public void operationImpl() {\n        System.out.println("Implementierung B");\n    }\n}'], 'client_code': 'public class Client {\n    public static void main(String[] args) {\n        Implementor implA = new ConcreteImplementorA();\n        Abstraction abstraction = new Abstraction(implA);\n        abstraction.operation(); // Ausgabe: "Implementierung A"\n        \n        // Dynamischer Austausch der Implementierung\n        abstraction = new Abstraction(new ConcreteImplementorB());\n        abstraction.operation(); // Ausgabe: "Implementierung B"\n    }\n}'}}
