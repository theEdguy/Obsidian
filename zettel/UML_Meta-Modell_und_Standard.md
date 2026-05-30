---
id: 5cfcbf3d-ee70-478b-960f-3a2796264bc3
title: "UML_Meta-Modell_und_Standard"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - meta-modellierung
  - softwarearchitektur
  - modellierung
  - omg_standard
  - draft
source: "Klausur_Referenz"
---

# [[UML_Meta-Modell_und_Standard]]

- **Kernkonzept:** Die **Unified Modeling Language (UML)** ist eine standardisierte, grafische Modellierungssprache zur Spezifikation, Konstruktion und Dokumentation von Software-Systemen. Sie basiert auf einem **[[Meta-Modell]]**, das alle Beschreibungselemente (z. B. Klassen, Assoziationen, Zustände) formal definiert und selbst in UML-Notation dargestellt wird. Dieses Meta-Modell ermöglicht Erweiterungen (z. B. durch **[[Stereotypen]]** oder **[[Profile]]**) und gewährleistet methodische Durchgängigkeit im **[[Softwareentwicklungsprozess]]**. UML wird von der **Object Management Group (OMG)** gepflegt und umfasst verschiedene Diagrammtypen wie **[[Klassendiagramm]]**, **[[Sequenzdiagramm]]** oder **[[Zustandsdiagramm]]**.
- **Nutzen & Zweck:** UML dient als **lingua franca** der Software-Entwicklung und ermöglicht:
- **Kommunikation**: Einheitliche Darstellung von Architektur und Design für Entwickler, Architekten und Stakeholder.
- **Abstraktion**: Modellierung komplexer Systeme auf verschiedenen Ebenen (z. B. Analyse vs. Implementierung).
- **Tool-Unterstützung**: Integration in **[[CASE-Tools]]** (z. B. Enterprise Architect, PlantUML) für Code-Generierung oder Reverse Engineering.
- **Dokumentation**: Konsistente Beschreibung von **[[Entwurfsmustern]]** (z. B. [[Singleton_Pattern]]) oder Systemverhalten.
- **Standardisierung**: Vermeidung von Missverständnissen durch präzise Syntax und Semantik (z. B. Multiplizitäten in **[[Assoziationen]]**).
- **Abgrenzung & Grenzen:** - **Keine Programmiersprache**: UML beschreibt *was* modelliert wird, nicht *wie* es implementiert wird (z. B. keine Algorithmen).
- **Kein Vorgehensmodell**: UML ist unabhängig von Methoden wie **[[Unified_Process]]** oder **[[Scrum]]**, kann aber darin eingebettet werden.
- **Komplexität**: Überladene Diagramme (z. B. zu viele Details in einem **[[Klassendiagramm]]**) können die Verständlichkeit beeinträchtigen.
- **Semantische Lücken**: Manche Konzepte (z. B. **[[Aspektorientierte_Programmierung]]**) erfordern Erweiterungen des Meta-Modells.
- **Tool-Abhängigkeit**: Unterschiedliche Tools interpretieren UML-Syntax teilweise inkonsistent (z. B. bei **[[OCL]]**-Ausdrücken).
- **Beispiel / Code:** ```mermaid
classDiagram
    class UML_MetaModell {
        +String name
        +Package ownedElements
        +erweitereMit(Stereotyp stereotype)
    }
    class Klasse {
        +String name
        +Attribute[] attributes
        +Operation[] operations
    }
    class Assoziation {
        +Klasse source
        +Klasse target
        +int multiplicity
    }
    UML_MetaModell "1" *-- "0..*" Klasse : enthält
    UML_MetaModell "1" *-- "0..*" Assoziation : enthält
    Klasse "1" -- "0..*" Assoziation : verknüpft
    note for Assoziation "Beispiel: Multiplizität 1..* für eine
    bidirektionale Beziehung zwischen Klassen"
```

**Erläuterung**: Das Mermaid-Diagramm zeigt einen Ausschnitt des UML-Meta-Modells. Die Klasse `UML_MetaModell` enthält `Klasse`- und `Assoziation`-Elemente, die selbst wieder in UML beschrieben werden. Dies illustriert die **Selbstbeschreibungsfähigkeit** von UML.
