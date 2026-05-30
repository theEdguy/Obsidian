---
id: 46214c80-8da7-4bbc-a175-f57a4ab6b5ba
title: "Entitaet"
date: 2026-05-30
tags:
  - software_engineering
  - domain_driven_design
  - entwurfsmuster
  - uml
  - softwarearchitektur
  - objektorientierung
  - draft
source: "Klausur_Referenz"
---

# [[Entitaet]]

- **Kernkonzept:** Eine **Entität** ist ein zentrales Konzept im [[Domain-Driven_Design]] und der [[Softwarearchitektur]], das ein eindeutig identifizierbares, in sich geschlossenes Objekt der realen oder fachlichen Domäne repräsentiert. Sie besitzt eine eindeutige Identität (z. B. durch eine ID), die über ihren gesamten Lebenszyklus hinweg konstant bleibt, unabhängig von Änderungen ihrer Attribute oder Zustände. Entitäten modellieren oft Geschäftsobjekte wie `Kunde`, `Bestellung` oder `Produkt` und kapseln sowohl Daten als auch die damit verbundenen [[Verantwortlichkeiten]] (z. B. Validierung, Berechnungen oder Geschäftslogik). Im Gegensatz zu [[Wertobjekten]] steht bei Entitäten nicht die Gleichheit der Attribute, sondern die Identität im Vordergrund.
- **Nutzen & Zweck:** - **Modellierung der Fachdomäne**: Entitäten ermöglichen eine präzise Abbildung realer Geschäftsobjekte und deren Beziehungen (z. B. in [[Klassendiagrammen]] oder [[Entity-Relationship-Modellen]]).
- **Trennung von Verantwortlichkeiten**: Durch die Kapselung von Daten und Logik in Entitäten wird die [[Separation_of_Concerns]] gefördert, was die Wartbarkeit und Testbarkeit verbessert.
- **Wiederverwendung und Standardisierung**: Entitäten dienen als Bausteine für [[Entwurfsmuster]] wie [[Repository_Pattern]] oder [[Aggregate_Root]], um konsistente Zugriffe auf Daten zu gewährleisten.
- **Dokumentation von Entwurfsentscheidungen**: Die explizite Definition von Entitäten (z. B. in [[UML]]-Diagrammen) erleichtert die Kommunikation im Team und die Nachvollziehbarkeit von Architekturentscheidungen.
- **Unterstützung von [[Use_Cases]]**: Entitäten bilden die Grundlage für die Strukturierung von Anwendungsfällen, indem sie die beteiligten Akteure und Datenobjekte klar definieren.
- **Abgrenzung & Grenzen:** - **Keine reinen Datencontainer**: Entitäten sollten nicht nur Attribute enthalten, sondern auch domänenspezifische Logik (z. B. Validierung oder Berechnungen). Reine `Data Transfer Objects` ([[DTO]]) sind keine Entitäten.
- **Identität vs. Gleichheit**: Die Identität einer Entität ist unabhängig von ihren Attributwerten. Zwei Entitäten mit identischen Attributen sind nicht zwangsläufig dieselbe Entität (z. B. zwei `Kunde`-Objekte mit gleicher Adresse, aber unterschiedlichen IDs).
- **Lebenszyklus**: Entitäten haben einen definierten Lebenszyklus (Erstellung, Änderung, Löschung), der oft durch [[Aggregate_Root]] oder [[Repository_Pattern]] gesteuert wird. Sie sollten nicht direkt aus der Persistenzschicht (z. B. Datenbank) instanziiert werden, ohne die Geschäftslogik zu berücksichtigen.
- **Keine technischen Details**: Entitäten sollten keine frameworkspezifischen Abhängigkeiten (z. B. JPA-Annotationen) enthalten, um die Domänenlogik von technischen Aspekten zu trennen (siehe [[Infrastructure_Ignorance]]).
- **Beispiel / Code:** {'beschreibung': 'Ein Beispiel für eine `Bestellung`-Entität in Java, die die Identität und domänenspezifische Logik demonstriert:', 'code': 'public class Bestellung {\n    private final BestellungsId id;  // Eindeutige Identität (Wertobjekt)\n    private LocalDateTime datum;\n    private List<Bestellposition> positionen;\n    private Bestellstatus status;\n\n    public Bestellung(BestellungsId id, LocalDateTime datum) {\n        this.id = id;\n        this.datum = datum;\n        this.positionen = new ArrayList<>();\n        this.status = Bestellstatus.ERSTELLT;\n    }\n\n    // Domänenlogik: Fügt eine Position hinzu und aktualisiert den Status\n    public void fuegePositionHinzu(Produkt produkt, int menge) {\n        if (status != Bestellstatus.ERSTELLT) {\n            throw new IllegalStateException("Bestellung kann nicht mehr geändert werden.");\n        }\n        positionen.add(new Bestellposition(produkt, menge));\n    }\n\n    // Domänenlogik: Berechnet den Gesamtpreis\n    public Geld berechneGesamtpreis() {\n        return positionen.stream()\n                .map(Bestellposition::berechnePreis)\n                .reduce(Geld.ZERO, Geld::addiere);\n    }\n\n    // Identität bleibt konstant, auch wenn Attribute sich ändern\n    public BestellungsId getId() {\n        return id;\n    }\n\n    // Weitere Methoden (z. B. Statusänderungen) folgen...\n}\n\n// Beispiel für ein Wertobjekt zur Identität\npublic record BestellungsId(String wert) {\n    public BestellungsId {\n        if (wert == null || wert.isBlank()) {\n            throw new IllegalArgumentException("ID darf nicht leer sein.");\n        }\n    }\n}', 'uml_diagramm': 'classDiagram\n    class Bestellung {\n        -BestellungsId id\n        -LocalDateTime datum\n        -List~Bestellposition~ positionen\n        -Bestellstatus status\n        +fuegePositionHinzu(produkt: Produkt, menge: int)\n        +berechneGesamtpreis() Geld\n        +getId() BestellungsId\n    }\n    class BestellungsId {\n        <<record>>\n        +wert: String\n    }\n    class Bestellposition {\n        -Produkt produkt\n        -int menge\n        +berechnePreis() Geld\n    }\n    class Produkt {\n        <<Entität>>\n        -ProduktId id\n        -String name\n        -Geld preis\n    }\n    Bestellung "1" *-- "0..*" Bestellposition\n    Bestellposition "1" --> "1" Produkt'}
