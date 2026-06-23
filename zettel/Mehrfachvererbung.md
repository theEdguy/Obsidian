---
id: 75b0bdfb-07f5-4d4e-80cb-e778be95ada6
title: "Mehrfachvererbung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - vererbung
  - cplusplus
  - entwurfsmuster
  - uml
  - diamantproblem
  - typen
  - draft
source: "software_engineering_kapitel_04"
---

# [[Mehrfachvererbung]]

- **Kernkonzept:** Mehrfachvererbung ist ein [[Konzept]] der [[objektorientierten_Programmierung|objektorientierten Programmierung]], bei dem eine [[Klasse]] von mehreren [[Basisklasse|Basisklassen]] erben kann, um deren [[Attribut|Attribute]] und [[Methode|Methoden]] zu übernehmen und zu kombinieren. Dadurch wird eine hierarchische Spezialisierung mit mehreren [[Elternklasse|Elternklassen]] ermöglicht, was die Modellierung komplexer [[Entität|Entitäten]] mit multiplen Rollen (z. B. ein `[[Amphibienfahrzeug]]`) erleichtert.
- **Nutzen & Zweck:** Mehrfachvererbung dient der Erhöhung von [[Code-Wiederverwendung|Code-Wiederverwendung]] und [[Modularität]] in der [[Softwareentwicklung]], indem eine [[Klasse]] Funktionalitäten aus verschiedenen [[Vererbungshierarchie|Vererbungshierarchien]] vereint. Sie löst das Problem der [[Einfachvererbung]], bei der eine [[Klasse]] nur von einer einzigen [[Oberklasse]] erben kann, und ermöglicht so die Abbildung realer Zusammenhänge (z. B. ein `[[Amphibienfahrzeug]]` als Kombination aus `[[Landfahrzeug]]` und `[[Wasserfahrzeug]]`). Typische Anwendungsfälle umfassen:

- Die Modellierung von [[Entität|Entitäten]] mit multiplen Rollen oder Eigenschaften (z. B. ein `[[Student]]`, der gleichzeitig `[[Mitarbeiter]]` ist).
- Die Implementierung von [[Mixin|Mixins]] oder [[Trait|Traits]], um wiederverwendbare Funktionalitäten (z. B. `[[Serializable]]`, `[[Cloneable]]`) in verschiedene [[Klasse|Klassen]] zu injizieren.
- Die Realisierung [[Schnittstelle|schnittstellenähnlicher]] Strukturen in Sprachen, die keine expliziten [[Schnittstelle|Schnittstellen]] unterstützen (z. B. C++).

Vorteile:
- **Flexibilität**: Ermöglicht die Komposition von [[Klasse|Klassen]] aus unterschiedlichen Domänen.
- **Redundanzvermeidung**: Fördert die Wiederverwendung existierender [[Implementierung|Implementierungen]] ohne Duplikation.
- **Ausdrucksstärke**: Erhöht die Modellierungsmöglichkeiten für komplexe Systeme.
- **Abgrenzung & Grenzen:** Mehrfachvererbung birgt mehrere Herausforderungen und sollte mit Bedacht eingesetzt werden:

- **[[Diamantproblem]]**: Tritt auf, wenn zwei [[Basisklasse|Basisklassen]] eine gemeinsame [[Oberklasse]] haben, was zu Mehrdeutigkeiten bei der Vererbung von [[Attribut|Attributen]] oder [[Methode|Methoden]] führt. Lösungen umfassen:
  - `virtual inheritance` in C++ (verhindert mehrfache Instanziierung der gemeinsamen [[Oberklasse]]).
  - Die Verwendung von [[Schnittstelle|Schnittstellen]] (z. B. in Java oder C#), die keine Implementierungen enthalten und somit keine Konflikte verursachen.
- **Komplexität**: Die [[Vererbungshierarchie|Vererbungshierarchien]] werden schwerer verständlich und wartbar, insbesondere bei tiefen oder zyklischen Abhängigkeiten. Dies kann gegen das Prinzip der [[Kohäsion]] verstoßen.
- **[[Kopplung]]**: Verstößt potenziell gegen das Prinzip der [[Lose_Kopplung|losen Kopplung]], da eine [[Klasse]] von mehreren anderen abhängt und Änderungen in den [[Basisklasse|Basisklassen]] direkte Auswirkungen auf die abgeleitete [[Klasse]] haben.
- **Sprachunterstützung**: Nicht alle [[Programmiersprache|Programmiersprachen]] unterstützen Mehrfachvererbung. Sprachen wie Java oder C# erlauben nur [[Einfachvererbung]] für [[Klasse|Klassen]], unterstützen aber die Mehrfachimplementierung von [[Schnittstelle|Schnittstellen]].

**Alternativen** zur Mehrfachvererbung:
- [[Komposition_über_Vererbung|Komposition über Vererbung]] (z. B. Delegation anstelle von Vererbung).
- [[Mixin|Mixins]] oder [[Trait|Traits]] (in Sprachen wie Scala, Ruby oder Python).
- [[Schnittstelle|Schnittstellen]] mit [[Default-Methode|Default-Methoden]] (ab Java 8).
- [[Entwurfsmuster]] wie [[Adapter]], [[Dekorierer]] oder [[Strategie]], um Funktionalitäten dynamisch zu kombinieren.
- **Beispiel / Code:** {'beschreibung': 'Beispiele in C++ (mit Lösung des [[Diamantproblem|Diamantproblems]] via `virtual inheritance`) und Java (als Alternative mit [[Schnittstelle|Schnittstellen]):', 'cplusplus': '```cpp\n#include <iostream>\nusing namespace std;\n\n// Basisklasse\nclass Fahrzeug {\npublic:\n    void bewegen() { cout << "Fahrzeug bewegt sich." << endl; }\n};\n\n// Erste abgeleitete Klasse (virtual inheritance)\nclass Landfahrzeug : virtual public Fahrzeug {\npublic:\n    void fahren() { cout << "Fährt an Land." << endl; }\n};\n\n// Zweite abgeleitete Klasse (virtual inheritance)\nclass Wasserfahrzeug : virtual public Fahrzeug {\npublic:\n    void schwimmen() { cout << "Schwimmt im Wasser." << endl; }\n};\n\n// Mehrfachvererbung: Amphibienfahrzeug erbt von beiden\nclass Amphibienfahrzeug : public Landfahrzeug, public Wasserfahrzeug {\npublic:\n    void nutzen() {\n        bewegen();  // Keine Mehrdeutigkeit dank virtual inheritance\n        fahren();\n        schwimmen();\n    }\n};\n\nint main() {\n    Amphibienfahrzeug af;\n    af.nutzen();\n    return 0;\n}\n```', 'java': '```java\n// Beispiel in Java mit Schnittstellen (keine Mehrfachvererbung für Klassen)\ninterface Landfahrzeug {\n    default void fahren() {\n        System.out.println("Fährt an Land.");\n    }\n}\n\ninterface Wasserfahrzeug {\n    default void schwimmen() {\n        System.out.println("Schwimmt im Wasser.");\n    }\n}\n\n// Klasse implementiert beide Schnittstellen\nclass Amphibienfahrzeug implements Landfahrzeug, Wasserfahrzeug {\n    public void nutzen() {\n        fahren();\n        schwimmen();\n    }\n}\n\npublic class Main {\n    public static void main(String[] args) {\n        Amphibienfahrzeug af = new Amphibienfahrzeug();\n        af.nutzen();\n    }\n}\n```', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Fahrzeug {\n        +bewegen()\n    }\n    class Landfahrzeug {\n        +fahren()\n    }\n    class Wasserfahrzeug {\n        +schwimmen()\n    }\n    class Amphibienfahrzeug {\n        +nutzen()\n    }\n    Fahrzeug <|-- Landfahrzeug : virtual\n    Fahrzeug <|-- Wasserfahrzeug : virtual\n    Landfahrzeug <|-- Amphibienfahrzeug\n    Wasserfahrzeug <|-- Amphibienfahrzeug\n```'}

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2
- **Vorgänger / Parent:** [[Vererbungstypen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
