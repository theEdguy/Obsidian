---
id: 7d33a443-a594-4c2e-89e6-688b2d8d9d9a
title: "Generalisierung_Vererbung"
date: 2026-05-31
tags:
  - software_engineering
  - objektorientierung
  - uml
  - entwurfsmuster
  - softwarearchitektur
  - solid_prinzipien
  - domain_driven_design
  - draft
source: "Klausur_Referenz"
---

# [[Generalisierung_Vererbung]]

- **Kernkonzept:** Generalisierung (auch als Vererbung bezeichnet) ist ein fundamentales Konzept der [[Objektorientierung]], bei dem eine [[Klasse]] (Subklasse) die Struktur und das Verhalten einer anderen Klasse (Superklasse) übernimmt und erweitern oder anpassen kann. Sie drückt eine „ist-ein“-Beziehung aus (z. B. „Ein Hund ist ein Tier“) und ermöglicht die Wiederverwendung von Code sowie die Modellierung von Hierarchien. In [[UML]] wird Generalisierung durch einen Pfeil mit geschlossener, nicht ausgefüllter Spitze dargestellt, der von der Subklasse zur Superklasse zeigt.
- **Nutzen & Zweck:** Generalisierung dient primär der **Code-Wiederverwendung** und der **Modellierung von Hierarchien**, um gemeinsame Eigenschaften und Methoden in einer Superklasse zu kapseln. Sie fördert die **Polymorphie**, indem Subklassen über [[Schnittstellen]] oder Superklassen referenziert werden können, was flexible und erweiterbare Systeme ermöglicht. Zudem unterstützt sie das **Open-Closed-Prinzip** ([[SOLID_Prinzipien]]), da neue Funktionalität durch Subklassen hinzugefügt werden kann, ohne bestehende Superklassen zu ändern. In der [[Softwarearchitektur]] wird Generalisierung oft eingesetzt, um Domänenmodelle (z. B. in [[Domain-Driven_Design]]) oder Frameworks (z. B. [[Template_Method_Pattern]]) zu strukturieren.
- **Abgrenzung & Grenzen:** Generalisierung ist **statisch** (zur Compile-Zeit festgelegt) und bindet Subklassen eng an die Implementierung der Superklasse, was die Flexibilität einschränken kann. Im Gegensatz dazu ermöglichen [[Objektkomposition]] und [[Delegation]] dynamische Beziehungen („hat-ein“ statt „ist-ein“), die zur Laufzeit geändert werden können. Typische Stolpersteine sind:
- **Fragile Base Class Problem**: Änderungen an der Superklasse können Subklassen brechen.
- **Übermäßige Vererbungstiefe**: Führt zu unübersichtlichen Hierarchien und Verletzungen des [[Single_Responsibility_Principle]].
- **Falsche Abstraktion**: Generalisierung sollte nur verwendet werden, wenn eine echte „ist-ein“-Beziehung vorliegt (z. B. ist ein Quadrat *kein* spezielles Rechteck, wenn Methoden wie `setBreite()` die Invariante brechen).
- **Verletzung des Liskovschen Substitutionsprinzips** ([[SOLID_Prinzipien]]): Subklassen müssen die Superklasse ohne unerwartetes Verhalten ersetzen können.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt Generalisierung in Java mit einer Superklasse `Tier` und einer Subklasse `Hund`. Die UML-Notation wird als Mermaid-Diagramm dargestellt:', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Tier {\n        +String name\n        +void fressen()\n    }\n    class Hund {\n        +void bellen()\n    }\n    Tier <|-- Hund : Generalisierung\n```', 'java_code': 'public class Tier {\n    protected String name;\n\n    public Tier(String name) {\n        this.name = name;\n    }\n\n    public void fressen() {\n        System.out.println(name + " frisst.");\n    }\n}\n\npublic class Hund extends Tier {\n    public Hund(String name) {\n        super(name); // Aufruf des Superklassen-Konstruktors\n    }\n\n    public void bellen() {\n        System.out.println(name + " bellt: Wuff!");\n    }\n\n    @Override\n    public void fressen() {\n        super.fressen(); // Wiederverwendung der Superklassen-Methode\n        System.out.println("Hunde fressen gerne Fleisch.");\n    }\n}\n\n// Nutzung der Polymorphie:\nTier meinTier = new Hund("Bello");\nmeinTier.fressen(); // Ruft die überschriebene Methode auf\n```', 'erlaeuterung': 'Die Subklasse `Hund` erbt das Attribut `name` und die Methode `fressen()` von `Tier`, überschreibt `fressen()` und fügt die Methode `bellen()` hinzu. Durch Polymorphie kann ein `Hund`-Objekt als `Tier` behandelt werden, was die Flexibilität erhöht.'}
