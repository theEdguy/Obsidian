---
id: 347a9b8c-b778-4f1f-a98a-ddcc7af8fcc3
title: "Entitaet"
date: 2026-05-31
tags:
  - software_engineering
  - domain_driven_design
  - entwurfsmuster
  - uml
  - datenmodellierung
  - objektorientierung
  - draft
source: "Klausur_Referenz"
---

# [[Entitaet]]

- **Kernkonzept:** Eine **Entität** ist ein zentrales Konzept in der [[Softwaremodellierung]] und [[Datenmodellierung]], das ein eindeutig identifizierbares Objekt der realen Welt oder des Problembereichs repräsentiert. Sie besitzt eine klare **Identität** (z. B. durch einen Primärschlüssel) und einen **Zustand**, der durch Attribute beschrieben wird. Entitäten kapseln **Verantwortlichkeiten** (z. B. Datenhaltung, Geschäftslogik) und interagieren über definierte [[Schnittstellen]] mit anderen Entitäten oder Komponenten. Im Kontext von [[Domain-Driven_Design]] (DDD) wird zwischen **Entitätsobjekten** (mit Identität) und [[Wertobjekten]] (ohne Identität, nur durch Attribute definiert) unterschieden.
- **Nutzen & Zweck:** 1. **Strukturierung von Domänenwissen**: Entitäten helfen, komplexe Systeme in handhabbare Einheiten zu zerlegen, indem sie reale Objekte (z. B. `Kunde`, `Bestellung`) abbilden und deren Beziehungen modellieren (z. B. über [[Assoziationen]] in [[Klassendiagrammen]]).
2. **Wiederverwendung und Wartbarkeit**: Durch die Kapselung von Verantwortlichkeiten in Entitäten lassen sich bewährte [[Entwurfsmuster]] (z. B. [[Repository_Pattern]]) anwenden, was die Codequalität und Erweiterbarkeit verbessert.
3. **Dokumentation von Entwurfsentscheidungen**: Entitäten machen implizites Wissen explizit (z. B. durch klare Benennung von Attributen und Methoden) und erleichtern so die Kommunikation im Team (vgl. [[Ubiquitous_Language]] in DDD).
4. **Datenkonsistenz**: Durch die Zuweisung von Verantwortlichkeiten (z. B. Validierung von Attributen) wird sichergestellt, dass Entitäten nur gültige Zustände annehmen (vgl. [[Invarianten]]).
- **Abgrenzung & Grenzen:** 1. **Keine reine Datenhaltung**: Eine Entität ist mehr als ein einfaches Datenobjekt (z. B. ein DTO). Sie sollte Geschäftslogik kapseln und nicht nur passive Daten speichern (Stolperfalle: *Anämisches_Domänenmodell*).
2. **Identität vs. Gleichheit**: Zwei Entitäten mit identischen Attributwerten sind nicht zwangsläufig dieselbe Entität (z. B. zwei `Kunde`-Objekte mit gleicher Adresse, aber unterschiedlicher ID). Dies grenzt sie von [[Wertobjekten]] ab.
3. **Keine UI- oder Infrastrukturlogik**: Entitäten sollten keine Abhängigkeiten zu technischen Schichten (z. B. Datenbankzugriff, UI-Frameworks) enthalten, um die [[Trennung_der_Zustaendigkeiten]] zu wahren.
4. **Komplexität bei Beziehungen**: Viele Entitäten mit bidirektionalen Beziehungen können zu zyklischen Abhängigkeiten führen (Lösungsansatz: [[Aggregat]] in DDD).
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer `Bestellung`-Entität in Java (DDD-konform), die Geschäftslogik kapselt und Invarianten sichert:', 'code': 'public class Bestellung {\n    private final BestellId id;          // Eindeutige Identität (Wertobjekt)\n    private final Kunde kunde;          // Assoziation zu einer anderen Entität\n    private final List<Bestellposition> positionen;\n    private Bestellstatus status;\n\n    public Bestellung(Kunde kunde) {\n        this.id = BestellId.neu();\n        this.kunde = kunde;\n        this.positionen = new ArrayList<>();\n        this.status = Bestellstatus.ERSTELLT;\n        // Invariante: Eine Bestellung muss mindestens eine Position haben\n        if (positionen.isEmpty()) {\n            throw new IllegalStateException("Eine Bestellung benötigt Positionen.");\n        }\n    }\n\n    public void hinzufuegenPosition(Produkt produkt, int menge) {\n        // Geschäftslogik: Menge prüfen\n        if (menge <= 0) {\n            throw new IllegalArgumentException("Menge muss positiv sein.");\n        }\n        positionen.add(new Bestellposition(produkt, menge));\n    }\n\n    public void bezahlen() {\n        if (status != Bestellstatus.ERSTELLT) {\n            throw new IllegalStateException("Nur erstellte Bestellungen können bezahlt werden.");\n        }\n        this.status = Bestellstatus.BEZAHLT;\n    }\n\n    // Getter (ohne Setter, um Zustandsänderungen zu kontrollieren)\n    public BestellId getId() { return id; }\n    public Bestellstatus getStatus() { return status; }\n}', 'uml_diagramm': 'classDiagram\n    class Bestellung {\n        -BestellId id\n        -Kunde kunde\n        -List~Bestellposition~ positionen\n        -Bestellstatus status\n        +hinzufuegenPosition(produkt: Produkt, menge: int)\n        +bezahlen()\n    }\n    class BestellId {\n        <<Wertobjekt>>\n    }\n    class Kunde {\n        <<Entität>>\n    }\n    class Bestellposition {\n        -Produkt produkt\n        -int menge\n    }\n    Bestellung "1" *-- "1..*" Bestellposition\n    Bestellung "1" --> "1" Kunde'}
