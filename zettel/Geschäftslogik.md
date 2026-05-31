---
id: 8974aae3-695d-43ec-9201-3ab03235be4b
title: "Geschäftslogik"
date: 2026-05-31
tags:
  - software_engineering
  - domain-driven_design
  - softwarearchitektur
  - entwurfsmuster
  - objektorientierung
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Geschäftslogik]]

- **Kernkonzept:** Geschäftslogik (auch Domänenlogik genannt) umfasst die Regeln, Prozesse und Berechnungen, die die fachlichen Anforderungen eines [[Softwaresystems]] abbilden. Sie definiert, wie Daten verarbeitet werden, um geschäftliche Ziele zu erreichen, und ist unabhängig von technischen Details wie [[Benutzeroberfläche]] oder [[Datenbank]]-Implementierung. Geschäftslogik wird oft in der [[Anwendungsschicht]] einer [[Mehrschichtenarchitektur]] angesiedelt und nutzt Konzepte wie [[Entitätsklassen]], [[Wertobjekte]] oder [[Aggregatwurzeln]] (aus [[Domain-Driven_Design]]), um die Domäne präzise zu modellieren.
- **Nutzen & Zweck:** 1. **Trennung von Belangen**: Geschäftslogik wird von technischen Aspekten (z. B. [[Persistenz]], UI) isoliert, was die Wartbarkeit und Testbarkeit erhöht.
2. **Wiederverwendbarkeit**: Dieselben Regeln können in verschiedenen Kontexten (z. B. Web-API, Batch-Verarbeitung) genutzt werden.
3. **Klarheit**: Durch die Fokussierung auf die Domäne wird die Kommunikation mit Fachexperten erleichtert (vgl. [[Ubiquitous_Language]]).
4. **Konsistenz**: Zentrale Logik verhindert Duplikate und Widersprüche in der Datenverarbeitung.

Beispiele: Berechnung von Rabatten, Validierung von Bestellungen, Workflows für Genehmigungsprozesse.
- **Abgrenzung & Grenzen:** - **Keine technische Logik**: Geschäftslogik enthält keine Details zu Datenbankzugriffen, Netzwerkkommunikation oder UI-Rendering (vgl. [[Infrastrukturschicht]]).
- **Keine Präsentation**: Formatierungen oder Benutzerinteraktionen gehören nicht zur Geschäftslogik.
- **Stolpersteine**: 
  - *Anämisches Domänenmodell*: Klassen mit nur Gettern/Settern, aber ohne Logik (Verstoß gegen [[Objektorientierung]]).
  - *Vermischung mit [[Anwendungslogik]]*: Geschäftslogik sollte nicht mit Koordinationsaufgaben (z. B. Transaktionsmanagement) überladen werden.
  - *Übermäßige Abhängigkeiten*: Geschäftslogik sollte keine direkten Abhängigkeiten zu Frameworks haben (vgl. [[Dependency_Inversion_Principle]]).
- **Beispiel / Code:** {'beschreibung': 'UML-Klassendiagramm (Mermaid-Syntax) und Java-Code zur Veranschaulichung einer Geschäftslogik für eine Bestellung mit Rabattberechnung:', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Bestellung {\n        -bestellNr: String\n        -positionen: List~Bestellposition~\n        +berechneGesamtpreis() BigDecimal\n        +istRabattfähig() boolean\n    }\n    \n    class Bestellposition {\n        -artikel: Artikel\n        -menge: int\n        +berechnePositionspreis() BigDecimal\n    }\n    \n    class Artikel {\n        -artikelNr: String\n        -preis: BigDecimal\n        -kategorie: Kategorie\n    }\n    \n    class Rabattregel {\n        <<interface>>\n        +berechneRabatt(bestellung: Bestellung) BigDecimal\n    }\n    \n    class Mengenrabatt {\n        +berechneRabatt(bestellung: Bestellung) BigDecimal\n    }\n    \n    Bestellung "1" *-- "1..*" Bestellposition\n    Bestellposition "1" --> "1" Artikel\n    Bestellung ..> Rabattregel : nutzt\n    Rabattregel <|.. Mengenrabatt\n```', 'java_code': 'public class Bestellung {\n    private String bestellNr;\n    private List<Bestellposition> positionen;\n    \n    public BigDecimal berechneGesamtpreis() {\n        BigDecimal summe = positionen.stream()\n            .map(Bestellposition::berechnePositionspreis)\n            .reduce(BigDecimal.ZERO, BigDecimal::add);\n        \n        if (istRabattfähig()) {\n            Rabattregel rabattregel = new Mengenrabatt();\n            BigDecimal rabatt = rabattregel.berechneRabatt(this);\n            summe = summe.subtract(rabatt);\n        }\n        return summe;\n    }\n    \n    public boolean istRabattfähig() {\n        return positionen.size() >= 5;\n    }\n}\n\npublic interface Rabattregel {\n    BigDecimal berechneRabatt(Bestellung bestellung);\n}\n\npublic class Mengenrabatt implements Rabattregel {\n    @Override\n    public BigDecimal berechneRabatt(Bestellung bestellung) {\n        return bestellung.berechneGesamtpreis().multiply(new BigDecimal("0.1"));\n    }\n}'}
