---
id: 67a892ad-fe9a-4153-b65f-90c74cc6f796
title: "Objektorientierte_Programmierung"
date: 2026-05-31
tags:
  - software_engineering
  - programmierparadigma
  - entwurfsmuster
  - uml
  - softwarearchitektur
  - modularisierung
  - vererbung
  - polymorphismus
  - draft
source: "Klausur_Referenz"
---

# [[Objektorientierte_Programmierung]]

- **Kernkonzept:** Die **Objektorientierte_Programmierung** (OOP) ist ein Programmierparadigma, das auf der Modellierung von Software als Sammlung interagierender [[Objekte]] basiert. Diese Objekte sind Instanzen von [[Klassen]], die sowohl Daten (Attribute) als auch Verhalten (Methoden) kapseln. OOP ermöglicht eine strukturierte, modularisierte und wiederverwendbare Softwareentwicklung durch zentrale Prinzipien wie [[Vererbung]], [[Polymorphismus]], [[Kapselung]] und [[Abstraktion]]. Ein zentrales Ziel ist die Abbildung realer Domänen in ein technisches System, wobei Konzepte wie [[Fabrikmethode]] oder [[Komposition]] die Flexibilität und Wartbarkeit erhöhen.
- **Nutzen & Zweck:** OOP wird eingesetzt, um komplexe Systeme durch **Modularisierung** und **Wiederverwendung** beherrschbar zu machen. Vorteile umfassen:
- **Erhöhte Wartbarkeit**: Durch klare Trennung von Verantwortlichkeiten (z. B. via [[Schnittstelle]] oder [[Design_by_Contract]]) lassen sich Änderungen lokal begrenzen.
- **Flexibilität**: Mechanismen wie [[Polymorphismus]] oder [[Strategie_Pattern]] ermöglichen dynamische Anpassungen zur Laufzeit.
- **Domänenorientierung**: Die Abbildung realer Entitäten (z. B. `Kunde`, `Bestellung`) in [[Klassen]] verbessert die Verständlichkeit und Kommunikation mit Stakeholdern.
- **Wiederverwendung**: Durch [[Vererbung]] oder [[Komposition]] (z. B. [[Decorator_Pattern]]) lassen sich bestehende Komponenten erweitern.

Typische Anwendungsfälle sind die Entwicklung von [[Softwarearchitektur]]en (z. B. [[Schichtenarchitektur]]), die Implementierung von [[Entwurfsmuster]]n oder die Modellierung von Geschäftsprozessen via [[UML]] (z. B. [[Klassendiagramm]]).
- **Abgrenzung & Grenzen:** OOP ist **kein Allheilmittel** und hat klare Grenzen:
- **Überengineering**: Unnötige Abstraktionen (z. B. zu tiefe [[Vererbung]]shierarchien) erhöhen die Komplexität ohne Mehrwert.
- **Performance-Overhead**: Dynamische Mechanismen wie [[Polymorphismus]] oder [[Reflection]] können die Laufzeiteffizienz beeinträchtigen (im Vergleich zu prozeduraler Programmierung).
- **Steile Lernkurve**: Konzepte wie [[Duck_Typing]] oder [[Metaprogrammierung]] erfordern tiefes Verständnis.
- **Nicht für alle Probleme geeignet**: Datenflussorientierte Systeme (z. B. ETL-Prozesse) lassen sich oft besser mit funktionaler Programmierung abbilden.

Stolpersteine:
- **Falsche Abstraktion**: Zu frühe oder zu späte Einführung von [[Schnittstelle]]n oder [[Abstrakte_Klasse]]n.
- **Verletzung der [[Kapselung]]**: Direkter Zugriff auf Attribute statt Nutzung von Gettern/Settern.
- **Missbrauch von [[Vererbung]]**: Verwendung für Code-Wiederverwendung statt für „is-a“-Beziehungen (besser: [[Komposition]]).
- **Unklare Verantwortlichkeiten**: Verletzung des [[Single_Responsibility_Principle]] (SRP) durch überladene [[Klassen]].
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer [[Fabrikmethode]] in Java, die die Erzeugung von Objekten an Unterklassen delegiert. Das Beispiel zeigt, wie eine `Dokument`-Klasse durch Unterklassen (`TextDokument`, `GrafikDokument`) erweitert wird, wobei die konkrete Erzeugung via `DokumentFabrik` erfolgt.', 'code': {'sprache': 'java', 'inhalt': 'public abstract class Dokument {\n    public abstract void oeffnen();\n    public abstract void speichern();\n}\n\npublic class TextDokument extends Dokument {\n    @Override\n    public void oeffnen() {\n        System.out.println("Textdokument geöffnet");\n    }\n    @Override\n    public void speichern() {\n        System.out.println("Textdokument gespeichert");\n    }\n}\n\npublic class GrafikDokument extends Dokument {\n    @Override\n    public void oeffnen() {\n        System.out.println("Grafikdokument geöffnet");\n    }\n    @Override\n    public void speichern() {\n        System.out.println("Grafikdokument gespeichert");\n    }\n}\n\npublic abstract class DokumentFabrik {\n    public abstract Dokument erstellenDokument();\n}\n\npublic class TextDokumentFabrik extends DokumentFabrik {\n    @Override\n    public Dokument erstellenDokument() {\n        return new TextDokument();\n    }\n}\n\npublic class GrafikDokumentFabrik extends DokumentFabrik {\n    @Override\n    public Dokument erstellenDokument() {\n        return new GrafikDokument();\n    }\n}\n\n// Nutzung:\nDokumentFabrik fabrik = new TextDokumentFabrik();\nDokument doc = fabrik.erstellenDokument();\ndoc.oeffnen(); // Ausgabe: "Textdokument geöffnet"'}, 'uml_diagramm': {'beschreibung': 'UML-Klassendiagramm zur Veranschaulichung der [[Fabrikmethode]] (vereinfacht).', 'mermaid_syntax': 'classDiagram\n    class Dokument {\n        <<abstract>>\n        +oeffnen()\n        +speichern()\n    }\n    class TextDokument {\n        +oeffnen()\n        +speichern()\n    }\n    class GrafikDokument {\n        +oeffnen()\n        +speichern()\n    }\n    class DokumentFabrik {\n        <<abstract>>\n        +erstellenDokument()* Dokument\n    }\n    class TextDokumentFabrik {\n        +erstellenDokument() Dokument\n    }\n    class GrafikDokumentFabrik {\n        +erstellenDokument() Dokument\n    }\n\n    Dokument <|-- TextDokument\n    Dokument <|-- GrafikDokument\n    DokumentFabrik <|-- TextDokumentFabrik\n    DokumentFabrik <|-- GrafikDokumentFabrik\n    DokumentFabrik ..> Dokument : erstellt\n    TextDokumentFabrik ..> TextDokument : erstellt\n    GrafikDokumentFabrik ..> GrafikDokument : erstellt'}}
