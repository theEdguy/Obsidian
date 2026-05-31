---
id: 7975bc82-7803-4c01-bda1-a3f5875fbcfb
title: "Mitglied_Persistentes_Objekt"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - domain_driven_design
  - datenmodellierung
  - persistenz
  - klassendiagramm
  - use_case
  - draft
source: "Klausur_Referenz"
---

# [[Mitglied_Persistentes_Objekt]]

- **Kernkonzept:** Ein **Mitglied** im Kontext der Softwareentwicklung bezeichnet eine [[Entitätsklasse]], die eine persistente, identifizierbare Einheit innerhalb eines Systems repräsentiert. Typischerweise modelliert es eine reale oder logische Entität (z. B. Nutzer, Kunde, Vereinsmitglied) mit Attributen (z. B. `name`, `adresse`) und Methoden (z. B. `leistungsprognose()`), die dessen Zustand und Verhalten kapseln. Der Stereotyp `<<persistent>>` kennzeichnet die Klasse als dauerhaft speicherbar, z. B. in einer [[Datenbank]] (hier: `Assocy.sqlite`).
- **Nutzen & Zweck:** Das Konzept dient der strukturierten Abbildung von Domänenobjekten in der [[Objektorientierten_Analyse_und_Design|OOAD]] und ermöglicht:
- **Datenkonsistenz**: Durch Kapselung von Attributen und Validierung (z. B. Constraints wie `{TableName <= 32}`).
- **Wiederverwendbarkeit**: Mitgliedsklassen können in verschiedenen [[Use-Case]]s (z. B. Leistungsprognose, Adressverwaltung) genutzt werden.
- **Persistenz**: Automatisierte Speicherung in Datenbanken via [[ORM]] (z. B. JPA/Hibernate).
- **Dokumentation**: UML-Stereotype wie `<<persistent>>` verbessern die Lesbarkeit von [[Klassendiagramm|Klassendiagrammen]].
- **Abgrenzung & Grenzen:** - **Kein [[Wertobjekt]]**: Mitglieder haben eine eindeutige Identität (z. B. Primärschlüssel in der DB) und sind nicht austauschbar wie Wertetypen.
- **Kein [[Service]]**: Enthält keine domänenübergreifende Logik, sondern fokussiert auf den Zustand eines einzelnen Objekts.
- **Stolpersteine**: 
  - **Zyklische Abhängigkeiten**: Bei Beziehungen zwischen Mitgliedern (z. B. `Mitglied → Team → Mitglied`) kann es zu Ladeproblemen kommen.
  - **Performance**: Persistente Objekte erfordern effizientes [[Lazy_Loading]] oder [[Caching]].
  - **Constraints**: DB-spezifische Regeln (z. B. `TableName <= 32`) müssen im Code validiert werden, um Inkonsistenzen zu vermeiden.
- **Beispiel / Code:** {'uml_klassendiagramm': '```mermaid\nclassDiagram\n    class Mitglied {\n        <<persistent>>\n        {TableName = Mitglied, SQLFile = Assocy.sqlite}\n        +name: String\n        #adresse: Anschrift\n        -alter: Date\n        -leistung: Integer = 1\n        +Mitglied(in name: String[2..*])\n        +leistungsprognose(datum: Date): Integer\n    }\n    class Anschrift {\n        +strasse: String\n        +plz: String\n        +ort: String\n    }\n    Mitglied --> Anschrift : enthält\n```', 'java_implementation': 'public class Mitglied {\n    // Persistente Attribute (gemappt auf DB-Spalten)\n    @Column(length = 32)  // Constraint aus UML\n    private String name;\n    \n    @Embedded  // Anschrift als Wertetyp\n    private Anschrift adresse;\n    \n    @Column(name = "geburtsdatum")\n    private LocalDate alter;\n    \n    @Column(columnDefinition = "INTEGER DEFAULT 1")\n    private int leistung = 1;\n    \n    // Konstruktor mit Validierung\n    public Mitglied(String name) {\n        if (name == null || name.length() < 2) {\n            throw new IllegalArgumentException("Name muss mindestens 2 Zeichen haben.");\n        }\n        this.name = name;\n    }\n    \n    // Domänenlogik\n    public int leistungsprognose(LocalDate datum) {\n        // Beispiel: Prognose basierend auf Alter und aktueller Leistung\n        return (int) (leistung * (1 + (Period.between(alter, datum).getYears() * 0.05)));\n    }\n}\n\n@Embeddable\npublic class Anschrift {\n    private String strasse;\n    private String plz;\n    private String ort;\n}', 'use_case_diagramm': '```mermaid\nuseCaseDiagram\n    actor "App-Entwickler" as dev\n    actor "Datenbank" as db\n    \n    usecase "Mitglied anlegen" as UC1\n    usecase "Leistung prognostizieren" as UC2\n    usecase "Adresse aktualisieren" as UC3\n    usecase "Mitglied in DB speichern" as UC4\n    \n    dev --> UC1\n    dev --> UC2\n    dev --> UC3\n    UC1 ..> UC4 : <<include>>\n    UC3 ..> UC4 : <<include>>\n    UC4 --> db\n```'}
