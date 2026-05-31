---
id: 62935c40-801e-4470-aa61-7a593ea2fee7
title: "Generalisierung_UML"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - objektorientierung
  - vererbung
  - klassendiagramm
  - entwurfsmuster
  - draft
source: "Klausur_Referenz"
---

# [[Generalisierung_UML]]

- **Kernkonzept:** Die [[Generalisierung]] in UML ist eine Beziehung zwischen einem allgemeinen Element (Superklasse oder Elternklasse) und einem spezielleren Element (Subklasse oder Kindklasse), bei der die Subklasse alle Eigenschaften, Operationen und Assoziationen der Superklasse erbt und diese erweitern oder überschreiben kann. Sie modelliert eine "ist-ein"-Beziehung (z. B. ein `Hund` ist ein `Tier`) und wird durch einen geschlossenen, nicht ausgefüllten Pfeil von der Subklasse zur Superklasse dargestellt. Generalisierung fördert die Wiederverwendung von Code und die hierarchische Strukturierung von [[Klassendiagrammen]].
- **Nutzen & Zweck:** Generalisierung dient der Abstraktion und Strukturierung von Modellen, indem gemeinsame Merkmale in einer Superklasse gebündelt werden. Dies reduziert Redundanzen, verbessert die Wartbarkeit und ermöglicht [[Polymorphismus]], bei dem Subklassen einheitlich über die Schnittstelle der Superklasse angesprochen werden können. Typische Anwendungsfälle sind:
- Modellierung von Vererbungshierarchien (z. B. `Fahrzeug` → `Auto`, `Fahrrad`).
- Implementierung von [[Entwurfsmustern]] wie [[Template_Method_Pattern]] oder [[Strategy_Pattern]].
- Definition von Schnittstellen (via [[Schnittstelle]]) mit gemeinsamen Operationen für verschiedene Implementierungen.
- **Abgrenzung & Grenzen:** Generalisierung ist abzugrenzen von:
- **[[Assoziation]]/[[Aggregation]]/[[Komposition]]**: Diese modellieren "hat-ein"-Beziehungen (z. B. `Auto` hat einen `Motor`), während Generalisierung eine "ist-ein"-Beziehung darstellt.
- **[[Realisierung]] (Interface-Implementierung)**: Hier wird eine [[Schnittstelle]] umgesetzt, ohne Vererbung von Implementierungsdetails.

Stolpersteine:
- **Tiefgreifende Hierarchien**: Zu viele Vererbungsebenen erschweren die Verständlichkeit und Wartung (vgl. [[Fragile_Base_Class_Problem]]).
- **Mehrfachvererbung**: UML erlaubt sie, aber viele Programmiersprachen (z. B. Java) unterstützen nur Einfachvererbung für Klassen.
- **Falsche Abstraktion**: Generalisierung sollte nur verwendet werden, wenn eine echte "ist-ein"-Beziehung vorliegt (z. B. ist ein `Quadrat` *kein* `Rechteck`, wenn `Rechteck` unveränderliche Seiten hat).
- **Beispiel / Code:** {'uml_beschreibung': '```mermaid\nclassDiagram\n    class Tier {\n        +String name\n        +void fressen()\n    }\n    class Hund {\n        +void bellen()\n    }\n    class Katze {\n        +void miauen()\n    }\n    Tier <|-- Hund\n    Tier <|-- Katze\n```', 'java_implementation': 'public abstract class Tier {\n    protected String name;\n    \n    public Tier(String name) {\n        this.name = name;\n    }\n    \n    public void fressen() {\n        System.out.println(name + " frisst.");\n    }\n}\n\npublic class Hund extends Tier {\n    public Hund(String name) {\n        super(name);\n    }\n    \n    public void bellen() {\n        System.out.println(name + " bellt: Wuff!");\n    }\n}\n\npublic class Katze extends Tier {\n    public Katze(String name) {\n        super(name);\n    }\n    \n    public void miauen() {\n        System.out.println(name + " miaut: Miau!");\n    }\n}', 'erlaeuterung': 'Im Beispiel erbt `Hund` und `Katze` von der Superklasse `Tier` die Attribute (`name`) und Methoden (`fressen()`). Beide Subklassen erweitern die Funktionalität durch eigene Methoden (`bellen()`, `miauen()`). Die UML-Notation zeigt die Generalisierung durch den Pfeil von der Sub- zur Superklasse.'}
