---
id: fa764d8f-eb49-4898-aa35-bfd197715045
title: "Generalisierung_Spezialisierung"
date: 2026-05-30
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

# [[Generalisierung_Spezialisierung]]

- **Kernkonzept:** Die [[Generalisierung_Spezialisierung]] ist ein fundamentales Prinzip in der objektorientierten Modellierung, das die Beziehung zwischen einer allgemeinen [[Basisklasse]] (Generalisierung) und einer oder mehreren spezifischeren [[Unterklasse]]n (Spezialisierungen) beschreibt. Dabei erbt die Spezialisierung alle Attribute und Methoden der Generalisierung und kann diese erweitern oder überschreiben. In [[UML]] wird diese Beziehung durch ein Dreieck (mit der Spitze zur Basisklasse) dargestellt und entspricht dem Konzept der [[Vererbung]] in Programmiersprachen.
- **Nutzen & Zweck:** Das Konzept dient der Strukturierung von [[Klassendiagramm]]men und fördert die Wiederverwendung von Code sowie die hierarchische Organisation von Domänenwissen. Durch Generalisierung_Spezialisierung lassen sich gemeinsame Eigenschaften und Verhalten zentral in einer Basisklasse definieren, während spezifische Ausprägungen in Unterklassen abgebildet werden. Dies reduziert Redundanzen und erleichtert die Wartbarkeit. Typische Anwendungsfälle sind:
- Modellierung von [[Entitätstyp]]en (z. B. `Tier` → `Hund`, `Katze`)
- Implementierung von [[Polymorphie]] (z. B. einheitliche Schnittstelle für verschiedene Algorithmen)
- Entwurf von [[Framework]]s oder [[Bibliothek]]en mit erweiterbaren Basisklassen.
- **Abgrenzung & Grenzen:** Generalisierung_Spezialisierung ist abzugrenzen von:
- **[[Assoziation]]/[[Aggregation]]/[[Komposition]]**: Diese beschreiben Beziehungen zwischen unabhängigen Klassen, während Generalisierung_Spezialisierung eine *ist-ein*-Beziehung (Subtyping) modelliert.
- **[[Schnittstelle]]n**: Schnittstellen definieren nur Verträge ohne Implementierung, während Basisklassen konkrete Funktionalität bereitstellen können.

Typische Stolpersteine:
- **Falsche Hierarchien**: Eine Spezialisierung sollte immer eine echte Teilmenge der Generalisierung sein (z. B. ist `Quadrat` keine sinnvolle Spezialisierung von `Rechteck`, wenn Verhalten überschrieben werden muss).
- **Tief verschachtelte Hierarchien**: Zu viele Vererbungsebenen erschweren die Verständlichkeit und Wartung (vgl. [[Fragile_Base_Class_Problem]]).
- **Missachtung des [[Liskov_Substitution_Principle]]**: Spezialisierungen müssen die Verträge der Basisklasse einhalten.
- **Verwechslung mit `include`/`extend` in [[Use_Case_Diagramm]]men**: Generalisierung_Spezialisierung bezieht sich auf Klassen, nicht auf Abläufe.
- **Beispiel / Code:** {'uml_diagramm': '```mermaid\nclassDiagram\n    class Fahrzeug {\n        +String hersteller\n        +int baujahr\n        +starten()\n        +bremsen()\n    }\n    class PKW {\n        +int anzahlSitze\n        +klimaanlageEin()\n    }\n    class LKW {\n        +double ladegewicht\n        +ladungSichern()\n    }\n    Fahrzeug <|-- PKW\n    Fahrzeug <|-- LKW\n```', 'java_implementation': 'public abstract class Fahrzeug {\n    protected String hersteller;\n    protected int baujahr;\n\n    public Fahrzeug(String hersteller, int baujahr) {\n        this.hersteller = hersteller;\n        this.baujahr = baujahr;\n    }\n\n    public void starten() {\n        System.out.println("Fahrzeug startet");\n    }\n\n    public abstract void bremsen();\n}\n\npublic class PKW extends Fahrzeug {\n    private int anzahlSitze;\n\n    public PKW(String hersteller, int baujahr, int anzahlSitze) {\n        super(hersteller, baujahr);\n        this.anzahlSitze = anzahlSitze;\n    }\n\n    @Override\n    public void bremsen() {\n        System.out.println("PKW bremst mit Scheibenbremsen");\n    }\n\n    public void klimaanlageEin() {\n        System.out.println("Klimaanlage aktiviert");\n    }\n}\n\npublic class LKW extends Fahrzeug {\n    private double ladegewicht;\n\n    public LKW(String hersteller, int baujahr, double ladegewicht) {\n        super(hersteller, baujahr);\n        this.ladegewicht = ladegewicht;\n    }\n\n    @Override\n    public void bremsen() {\n        System.out.println("LKW bremst mit Druckluftbremse");\n    }\n\n    public void ladungSichern() {\n        System.out.println("Ladung gesichert");\n    }\n}', 'erlaeuterung': 'Das Beispiel zeigt eine Generalisierung (`Fahrzeug`) mit zwei Spezialisierungen (`PKW`, `LKW`). Die Basisklasse definiert gemeinsame Attribute (`hersteller`, `baujahr`) und Methoden (`starten()`), während die Unterklassen spezifische Eigenschaften (`anzahlSitze`, `ladegewicht`) und Implementierungen (`bremsen()`) hinzufügen. Die abstrakte Methode `bremsen()` erzwingt eine konkrete Implementierung in den Spezialisierungen.'}
