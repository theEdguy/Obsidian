---
id: 7ca1b9b5-af42-48e3-8a8c-2978c57581d1
title: "Objektorientierte_Analyse_und_Design"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - entwurfsmuster
  - softwarearchitektur
  - anforderungsanalyse
  - systemmodellierung
  - draft
source: "Klausur_Referenz"
---

# [[Objektorientierte_Analyse_und_Design]]

- **Kernkonzept:** Objektorientierte_Analyse_und_Design (OOAD) ist ein methodischer Ansatz im [[Software_Engineering]], der die Prinzipien der [[Objektorientierung]] nutzt, um Software-Systeme zu modellieren und zu entwickeln. Die Analysephase konzentriert sich auf das **Verständnis und die Spezifikation der Anforderungen** aus fachlicher Sicht, während das Design die **technische Umsetzung** dieser Anforderungen in eine softwaretechnische Lösung fokussiert. Beide Phasen verwenden ähnliche [[UML]]-Diagramme (z. B. [[Klassendiagramm]], [[Aktivitätsdiagramm]], [[Sequenzdiagramm]]), unterscheiden sich jedoch in ihrer Zielsetzung und Detaillierungstiefe.
- **Nutzen & Zweck:** OOAD dient der strukturierten Entwicklung von Software-Systemen durch:
- **Analyse**: Identifikation von Fachklassen, Geschäftsprozessen und Systemanforderungen (z. B. durch [[Use_Case_Diagramme]]). Ziel ist es, ein **domänenspezifisches Modell** zu erstellen, das unabhängig von technischen Details ist.
- **Design**: Transformation des Analysemodells in ein **technisches Modell**, das Implementierungsdetails wie [[Schnittstellen]], Datenbankanbindungen oder [[Entwurfsmuster]] (z. B. [[Singleton_Pattern]], [[Factory_Method]]) berücksichtigt.

Vorteile:
- Klare Trennung von fachlichen und technischen Aspekten.
- Wiederverwendbarkeit durch [[Modularität]] und [[Kapselung]].
- Bessere Kommunikation zwischen Stakeholdern durch visuelle Modelle.
- **Abgrenzung & Grenzen:** 1. **Zielsetzung**: 
   - **Analyse**: Beschreibt **was** das System leisten soll (fachliche Perspektive). Beispiel: Ein [[Klassendiagramm]] zeigt Fachklassen wie `Kunde` oder `Bestellung` ohne technische Attribute.
   - **Design**: Beschreibt **wie** das System umgesetzt wird (technische Perspektive). Beispiel: Ein [[Klassendiagramm]] enthält technische Details wie `Datenbankverbindung` oder Methoden zur Persistenz.

2. **Detaillierungsgrad**: 
   - Analyse-Modelle sind **abstrakt** und implementierungsunabhängig.
   - Design-Modelle sind **konkret** und enthalten z. B. Algorithmen, Datenstrukturen oder [[API]]-Spezifikationen.

3. **Stolpersteine**: 
   - **Vermischung der Phasen**: Technische Entscheidungen (z. B. Wahl eines [[Frameworks]]) dürfen nicht in die Analyse einfließen.
   - **Übermodellierung**: Zu detaillierte Modelle in der Analyse führen zu unnötigem Aufwand.
   - **Unterschätzung der Komplexität**: Design erfordert oft Anpassungen an nicht-funktionale Anforderungen (z. B. [[Performance]], [[Sicherheit]]).
- **Beispiel / Code:** ```mermaid
classDiagram
    %% Analyse-Perspektive (fachlich)
    class Kunde {
        +String name
        +String adresse
        +bestellen(produkt: Produkt)
    }
    class Bestellung {
        +Datum datum
        +Status status
        +berechneGesamtpreis()
    }
    Kunde "1" -- "0..*" Bestellung

    %% Design-Perspektive (technisch)
    class KundeRepository {
        +save(kunde: Kunde)
        +findById(id: UUID)
    }
    class BestellService {
        +createBestellung(kundeId: UUID, produkte: List~Produkt~)
        +updateStatus(bestellId: UUID, status: Status)
    }
    KundeRepository --> Kunde : persistiert
    BestellService --> Bestellung : verwaltet
```

**Java-Code-Beispiel (Design-Phase)**:
```java
// Design: Technische Umsetzung mit Persistenz und Schnittstellen
public interface KundeRepository {
    void save(Kunde kunde);
    Kunde findById(UUID id);
}

public class BestellService {
    private final KundeRepository kundeRepository;
    private final BestellRepository bestellRepository;

    public BestellService(KundeRepository kundeRepository, BestellRepository bestellRepository) {
        this.kundeRepository = kundeRepository;
        this.bestellRepository = bestellRepository;
    }

    public Bestellung createBestellung(UUID kundeId, List<Produkt> produkte) {
        Kunde kunde = kundeRepository.findById(kundeId);
        Bestellung bestellung = new Bestellung(kunde, produkte);
        bestellRepository.save(bestellung);
        return bestellung;
    }
}
```
