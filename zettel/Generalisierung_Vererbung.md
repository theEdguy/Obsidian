---
id: 927e50fe-ff1b-4f1f-9dc6-c98c4cfd1e18
title: "Generalisierung_Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - uml
  - entwurfsmuster
  - softwarearchitektur
  - solid_prinzipien
  - domain_driven_design
  - vererbung
  - modellierung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Generalisierung_Vererbung]]

- **Kernkonzept:** Generalisierung (auch als [[Vererbung|Vererbungsbeziehung]] bezeichnet) ist ein fundamentales Konzept der [[Objektorientierung]], das sowohl in [[Klassen|Klassenhierarchien]] als auch in [[Use-Case-Diagramm|Use-Case-Diagrammen]] eingesetzt wird, um „ist-ein“-Beziehungen abzubilden. Sie ermöglicht die Wiederverwendung von Struktur und Verhalten durch [[Subklasse|Subklassen]] oder spezialisierte [[Use-Case|Use-Cases]], die von einer allgemeineren [[Superklasse]] oder einem Eltern-Use-Case erben und diese erweitern oder präzisieren.
- **Nutzen & Zweck:** Generalisierung dient primär der **Code-Wiederverwendung** und der **Modellierung von Hierarchien**, indem gemeinsame Eigenschaften und [[Methode|Methoden]] in einer [[Superklasse]] oder einem Eltern-Use-Case zentralisiert werden. In der [[Objektorientierung]] fördert sie [[Polymorphie]] und unterstützt das [[Open-Closed_Prinzip]] ([[SOLID_Prinzipien]]), da neue Funktionalität durch [[Subklasse|Subklassen]] oder spezialisierte Use-Cases hinzugefügt werden kann, ohne bestehende Implementierungen zu ändern. In [[Use-Case-Diagramm|Use-Case-Diagrammen]] reduziert sie Redundanz, indem sie eigenständige Varianten eines Anwendungsfalls abbildet und die Wartbarkeit verbessert. Zudem wird Generalisierung in der [[Softwarearchitektur]] genutzt, um [[Domänenmodell|Domänenmodelle]] (z. B. in [[Domain-Driven_Design]]) oder Frameworks (z. B. [[Template_Method_Pattern]]) zu strukturieren.
- **Abgrenzung & Grenzen:** Generalisierung ist **statisch** (zur Compile-Zeit festgelegt) und bindet [[Subklasse|Subklassen]] oder spezialisierte Use-Cases eng an die Implementierung der [[Superklasse]] oder des Eltern-Use-Cases, was die Flexibilität einschränken kann. Im Gegensatz dazu ermöglichen [[Objektkomposition]] und [[Delegation]] dynamische Beziehungen („hat-ein“ statt „ist-ein“), die zur Laufzeit geändert werden können. Typische Stolpersteine sind:

- **Fragile Base Class Problem**: Änderungen an der [[Superklasse]] können [[Subklasse|Subklassen]] oder abhängige Use-Cases brechen.
- **Übermäßige Vererbungstiefe**: Führt zu unübersichtlichen Hierarchien und Verletzungen des [[Single_Responsibility_Principle]].
- **Falsche Abstraktion**: Generalisierung sollte nur verwendet werden, wenn eine echte „ist-ein“-Beziehung vorliegt (z. B. ist ein Quadrat *kein* spezielles Rechteck, wenn [[Methode|Methoden]] wie `setBreite()` die Invariante brechen).
- **Verletzung des Liskovschen Substitutionsprinzips** ([[SOLID_Prinzipien]]): [[Subklasse|Subklassen]] oder spezialisierte Use-Cases müssen die [[Superklasse]] oder den Eltern-Use-Case ohne unerwartetes Verhalten ersetzen können.
- **Ungeeignete Anwendung in Use-Case-Diagrammen**: Generalisierung sollte vermieden werden, wenn die Unterschiede zwischen Use-Cases minimal sind oder sich besser durch `<<include>>`- oder `<<extend>>`-Beziehungen abbilden lassen. Sie ist ungeeignet, wenn die Spezialisierung keine eigenständige Bedeutung hat oder wenn zeitliche Abfolgen modelliert werden sollen, da [[Use-Case-Diagramm|Use-Case-Diagramme]] keine Ablaufreihenfolge darstellen.
- **Beispiel / Code:** {'beschreibung': 'Die folgenden Beispiele zeigen Generalisierung in verschiedenen Kontexten:', 'klassenhierarchie': {'uml_diagramm': '```mermaid\nclassDiagram\n    class Tier {\n        +String name\n        +void fressen()\n    }\n    class Hund {\n        +void bellen()\n    }\n    Tier <|-- Hund : Generalisierung\n```', 'java_code': 'public class Tier {\n    protected String name;\n\n    public Tier(String name) {\n        this.name = name;\n    }\n\n    public void fressen() {\n        System.out.println(name + " frisst.");\n    }\n}\n\npublic class Hund extends Tier {\n    public Hund(String name) {\n        super(name); // Aufruf des Superklassen-Konstruktors\n    }\n\n    public void bellen() {\n        System.out.println(name + " bellt: Wuff!");\n    }\n\n    @Override\n    public void fressen() {\n        super.fressen(); // Wiederverwendung der Superklassen-Methode\n        System.out.println("Hunde fressen gerne Fleisch.");\n    }\n}\n\n// Nutzung der Polymorphie:\nTier meinTier = new Hund("Bello");\nmeinTier.fressen(); // Ruft die überschriebene Methode auf\n```', 'erlaeuterung': 'Die [[Subklasse]] `Hund` erbt das Attribut `name` und die [[Methode]] `fressen()` von der [[Superklasse]] `Tier`, überschreibt `fressen()` und fügt die [[Methode]] `bellen()` hinzu. Durch [[Polymorphie]] kann ein `Hund`-Objekt als `Tier` behandelt werden, was die Flexibilität erhöht.'}, 'use_case_diagramm': {'uml_diagramm': '```mermaid\nusecaseDiagram\n    actor Kunde\n    Kunde --> (Zahlung durchführen)\n    (Zahlung durchführen) <|-- (Kreditkartenzahlung durchführen)\n```', 'erlaeuterung': 'Der spezialisierte Use-Case `Kreditkartenzahlung durchführen` erbt alle Eigenschaften und Beziehungen des Eltern-Use-Cases `Zahlung durchführen` und erweitert diesen um spezifische Validierungslogik für Kartendaten. Dies reduziert Redundanz und verbessert die Übersichtlichkeit des Modells.'}}

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3
- **Vorgänger / Parent:** [[Use_Case_Beziehungen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Beziehungen]]
  - [[Vererbung]]
