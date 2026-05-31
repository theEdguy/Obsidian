---
id: f4f12f0f-f60a-4013-9adc-552dbd83fc8d
title: "SOLID_Prinzipien"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - objektorientierte_programmierung
  - refaktorisierung
  - design_prinzipien
  - draft
source: "Klausur_Referenz"
---

# [[SOLID_Prinzipien]]

- **Kernkonzept:** Die SOLID-Prinzipien sind fünf grundlegende Richtlinien für den objektorientierten Entwurf ([[Objektorientierter_Entwurf]]), die darauf abzielen, Software modularer, wartbarer und erweiterbarer zu gestalten. Der Begriff ist ein Akronym und steht für:

1. **Single Responsibility Principle (SRP)**: Eine [[Klasse]] sollte nur eine einzige Verantwortlichkeit haben, d. h. nur einen Grund zur Änderung.
2. **Open-Closed Principle (OCP)**: Software-Entitäten (Klassen, Module, Funktionen) sollten offen für Erweiterungen, aber geschlossen für Modifikationen sein.
3. **Liskov Substitution Principle (LSP)**: Objekte einer [[Basisklasse]] sollten durch Objekte einer [[abgeleiteten_Klasse]] ersetzt werden können, ohne die Korrektheit des Programms zu beeinträchtigen.
4. **Interface Segregation Principle (ISP)**: Clients sollten nicht von [[Schnittstelle]]n abhängig sein, die sie nicht verwenden. Stattdessen sollten mehrere spezifische Schnittstellen einer einzigen allgemeinen vorgezogen werden.
5. **Dependency Inversion Principle (DIP)**: Abhängigkeiten sollten von Abstraktionen (z. B. [[Schnittstelle]]n) und nicht von konkreten Implementierungen abhängen.

Diese Prinzipien fördern lose Kopplung ([[Lose_Kopplung]]) und hohe Kohäsion ([[Kohäsion]]) in Softwaresystemen.
- **Nutzen & Zweck:** Die SOLID-Prinzipien dienen folgenden Zwecken:

- **Wartbarkeit**: Durch klare Trennung von Verantwortlichkeiten und Abhängigkeiten wird der Code leichter verständlich und änderbar.
- **Erweiterbarkeit**: Neue Funktionen können hinzugefügt werden, ohne bestehenden Code zu modifizieren (z. B. durch [[Entwurfsmuster]] wie [[Strategy_Pattern]] oder [[Decorator_Pattern]]).
- **Testbarkeit**: Lose gekoppelte Komponenten lassen sich einfacher isoliert testen (z. B. mit [[Unit_Tests]] und [[Mocking]]).
- **Wiederverwendbarkeit**: Modulare Designs ermöglichen die Wiederverwendung von Komponenten in anderen Kontexten.
- **Robustheit**: Durch Einhaltung von LSP und DIP wird die Wahrscheinlichkeit von Fehlern bei Erweiterungen reduziert.

Typische Anwendungsfälle sind die Entwicklung von [[Softwarearchitektur]]en, die Refaktorisierung von Legacy-Code oder die Planung von [[API]]-Designs.
- **Abgrenzung & Grenzen:** Die SOLID-Prinzipien sind **keine starren Regeln**, sondern Leitlinien, deren Anwendung kontextabhängig ist:

- **Überengineering**: Eine zu dogmatische Anwendung kann zu unnötiger Komplexität führen (z. B. zu viele kleine [[Schnittstelle]]n beim ISP).
- **Nicht für alle Projekte geeignet**: In kleinen oder kurzlebigen Projekten kann der Aufwand für SOLID-konforme Designs den Nutzen übersteigen.
- **Abhängigkeit von Abstraktionen**: DIP erfordert oft zusätzliche [[Abstraktionsschichten]], die die Codebasis vergrößern können.
- **Lernkurve**: Die Prinzipien setzen fundierte Kenntnisse in [[Objektorientierte_Programmierung]] und [[Design_Patterns]] voraus.
- **Trade-offs**: Beispielsweise kann SRP zu vielen kleinen Klassen führen, was die Übersichtlichkeit beeinträchtigen kann.

Stolpersteine:
- **Verwechslung von SRP mit „eine Klasse = eine Methode“**: SRP bezieht sich auf Verantwortlichkeiten, nicht auf die Anzahl der Methoden.
- **OCP falsch anwenden**: Nicht jede Erweiterung sollte durch Vererbung gelöst werden (z. B. ist [[Komposition]] oft besser).
- **LSP-Verletzungen**: Häufig bei falscher Verwendung von Vererbung (z. B. wenn eine [[abgeleitete_Klasse]] Vorbedingungen verschärft oder Nachbedingungen abschwächt).
- **Beispiel / Code:** {'sprache': 'Java', 'beschreibung': 'Beispiel für das **Open-Closed Principle (OCP)** und **Dependency Inversion Principle (DIP)**:\n\n1. **OCP**: Erweiterung durch [[Schnittstelle]]n und [[Komposition]] statt Modifikation.\n2. **DIP**: Abhängigkeit von einer Abstraktion (`BienenBestimmer`), nicht von konkreten Implementierungen.', 'code': '// Abstraktion (DIP: Abhängigkeit von Schnittstelle)\npublic interface BienenBestimmer {\n    String bestimmeArt(BienenDaten daten);\n}\n\n// Konkrete Implementierung 1\npublic class RegelbasierterBestimmer implements BienenBestimmer {\n    @Override\n    public String bestimmeArt(BienenDaten daten) {\n        // Logik zur Bestimmung basierend auf Regeln\n        return "Honigbiene";\n    }\n}\n\n// Konkrete Implementierung 2 (OCP: Erweiterung ohne Modifikation)\npublic class KIbasierterBestimmer implements BienenBestimmer {\n    @Override\n    public String bestimmeArt(BienenDaten daten) {\n        // Logik zur Bestimmung mittels KI\n        return "Wildbiene";\n    }\n}\n\n// Client-Klasse (DIP: Abhängigkeit von Abstraktion)\npublic class BienenApp {\n    private final BienenBestimmer bestimmer;\n\n    public BienenApp(BienenBestimmer bestimmer) {\n        this.bestimmer = bestimmer; // Injektion der Abhängigkeit\n    }\n\n    public void bestimmeUndSpeichere(BienenDaten daten) {\n        String art = bestimmer.bestimmeArt(daten);\n        System.out.println("Bestimmte Art: " + art);\n    }\n}\n\n// Verwendung\npublic class Main {\n    public static void main(String[] args) {\n        BienenBestimmer bestimmer = new KIbasierterBestimmer(); // Austauschbar\n        BienenApp app = new BienenApp(bestimmer);\n        app.bestimmeUndSpeichere(new BienenDaten());\n    }\n}', 'uml_diagramm': {'beschreibung': 'Klassendiagramm ([[Klassendiagramm]]) zur Veranschaulichung von OCP und DIP:', 'mermaid_syntax': 'classDiagram\n    class BienenBestimmer {\n        <<interface>>\n        +bestimmeArt(daten: BienenDaten) String\n    }\n\n    class RegelbasierterBestimmer {\n        +bestimmeArt(daten: BienenDaten) String\n    }\n\n    class KIbasierterBestimmer {\n        +bestimmeArt(daten: BienenDaten) String\n    }\n\n    class BienenApp {\n        -bestimmer: BienenBestimmer\n        +BienenApp(bestimmer: BienenBestimmer)\n        +bestimmeUndSpeichere(daten: BienenDaten) void\n    }\n\n    BienenBestimmer <|-- RegelbasierterBestimmer\n    BienenBestimmer <|-- KIbasierterBestimmer\n    BienenApp --> BienenBestimmer : depends on'}}
