---
id: aa1d5d7c-35c7-4596-b833-21834abdf18f
title: "Mehrfachvererbung"
date: 2026-05-31
tags:
  - software_engineering
  - objektorientierung
  - vererbung
  - cplusplus
  - entwurfsmuster
  - uml
  - diamantproblem
  - draft
source: "Klausur_Referenz"
---

# [[Mehrfachvererbung]]

- **Kernkonzept:** Mehrfachvererbung ist ein Konzept in der objektorientierten Programmierung (OOP), bei dem eine [[Klasse]] von mehreren [[Basisklassen]] erben kann. Dadurch übernimmt die abgeleitete Klasse die Attribute und Methoden aller Elternklassen und kann diese erweitern oder überschreiben. Im Gegensatz zur [[Einfachvererbung]] ermöglicht Mehrfachvererbung die Kombination von Funktionalitäten aus unterschiedlichen Vererbungshierarchien, was jedoch zu komplexen Abhängigkeiten führen kann.
- **Nutzen & Zweck:** Mehrfachvererbung wird eingesetzt, um Code-Wiederverwendung und Modularität zu erhöhen, indem eine Klasse Eigenschaften und Verhalten mehrerer [[Basisklassen]] vereint. Typische Anwendungsfälle sind:
- Modellierung von Entitäten mit multiplen Rollen (z. B. ein `Amphibienfahrzeug`, das sowohl `[[Landfahrzeug]]` als auch `[[Wasserfahrzeug]]` erbt).
- Implementierung von [[Mixins]], um wiederverwendbare Funktionalitäten (z. B. `Serializable`, `Cloneable`) in verschiedene Klassen zu injizieren.
- Realisierung von [[Schnittstellen]]-ähnlichen Strukturen in Sprachen, die keine expliziten Schnittstellen unterstützen (z. B. C++).

Vorteile:
- Flexibilität bei der Komposition von Klassen.
- Vermeidung von Redundanz durch Wiederverwendung existierender Implementierungen.
- **Abgrenzung & Grenzen:** Mehrfachvererbung birgt mehrere Herausforderungen und Grenzen:
- **Diamantproblem**: Wenn zwei [[Basisklassen]] eine gemeinsame Elternklasse haben, führt dies zu Mehrdeutigkeiten bei der Vererbung von Attributen/Methoden (z. B. in C++). Lösungen wie `virtual inheritance` oder die Verwendung von [[Schnittstellen]] (z. B. in Java) umgehen dieses Problem.
- **Komplexität**: Die Vererbungshierarchie wird schwerer verständlich und wartbar, insbesondere bei tiefen oder zyklischen Abhängigkeiten.
- **Kopplung**: Verstößt potenziell gegen das Prinzip der [[Lose_Kopplung]], da eine Klasse von mehreren anderen abhängt.
- **Sprachunterstützung**: Nicht alle OOP-Sprachen unterstützen Mehrfachvererbung (z. B. Java oder C# erlauben nur [[Einfachvererbung]] für Klassen, aber Mehrfachimplementierung von [[Schnittstellen]]).

Alternativen:
- [[Komposition_über_Vererbung]] (z. B. Delegation anstelle von Vererbung).
- [[Traits]] oder [[Mixins]] (in Sprachen wie Scala oder Ruby).
- [[Schnittstellen]] mit Default-Methoden (Java 8+).
- **Beispiel / Code:** {'beschreibung': 'Beispiel in C++ (mit Diamantproblem und Lösung via `virtual inheritance`):', 'code': '#include <iostream>\nusing namespace std;\n\n// Basisklasse\nclass Fahrzeug {\npublic:\n    void bewegen() { cout << "Fahrzeug bewegt sich." << endl; }\n};\n\n// Erste abgeleitete Klasse\nclass Landfahrzeug : virtual public Fahrzeug {\npublic:\n    void fahren() { cout << "Fährt an Land." << endl; }\n};\n\n// Zweite abgeleitete Klasse\nclass Wasserfahrzeug : virtual public Fahrzeug {\npublic:\n    void schwimmen() { cout << "Schwimmt im Wasser." << endl; }\n};\n\n// Mehrfachvererbung: Amphibienfahrzeug erbt von beiden\nclass Amphibienfahrzeug : public Landfahrzeug, public Wasserfahrzeug {\npublic:\n    void nutzen() {\n        bewegen();  // Keine Mehrdeutigkeit dank virtual inheritance\n        fahren();\n        schwimmen();\n    }\n};\n\nint main() {\n    Amphibienfahrzeug af;\n    af.nutzen();\n    return 0;\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Fahrzeug {\n        +bewegen()\n    }\n    class Landfahrzeug {\n        +fahren()\n    }\n    class Wasserfahrzeug {\n        +schwimmen()\n    }\n    class Amphibienfahrzeug {\n        +nutzen()\n    }\n    Fahrzeug <|-- Landfahrzeug : virtual\n    Fahrzeug <|-- Wasserfahrzeug : virtual\n    Landfahrzeug <|-- Amphibienfahrzeug\n    Wasserfahrzeug <|-- Amphibienfahrzeug\n```'}
