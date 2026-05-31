---
id: 99ec900a-95bb-4a1b-8e30-43fc73b87f84
title: "Systemdesign"
date: 2026-05-31
tags:
  - software_engineering
  - softwarearchitektur
  - uml
  - entwurfsmuster
  - modularisierung
  - systemanalyse
  - schnittstellen
  - draft
source: "Klausur_Referenz"
---

# [[Systemdesign]]

- **Kernkonzept:** Systemdesign ist der Prozess der Definition der [[Architektur]], Komponenten, Module, [[Schnittstellen]] und Daten eines Softwaresystems, um die spezifizierten [[funktionale_Anforderungen]] und nicht-funktionalen Anforderungen zu erfüllen. Es umfasst die Festlegung von [[Systemgrenzen]], die Strukturierung der Systeminteraktionen (z. B. durch [[System-Sequenz-Diagramm]]e) und die Zuweisung von Verantwortlichkeiten an Komponenten. Ziel ist es, ein robustes, wartbares und skalierbares System zu entwerfen, das die gewünschten Funktionen effizient umsetzt.
- **Nutzen & Zweck:** Systemdesign dient als Brücke zwischen der Anforderungsanalyse und der Implementierung. Es ermöglicht:
- Eine klare Trennung von Verantwortlichkeiten durch [[Modularisierung]].
- Die frühzeitige Identifikation von [[Schnittstellen]] und Abhängigkeiten, um spätere Integrationsprobleme zu vermeiden.
- Die Bewertung von [[Entwurfsmuster]]n und Architekturstilen (z. B. [[Schichtenarchitektur]], [[Microservices]]) zur Lösung spezifischer Probleme.
- Die Dokumentation der Systemstruktur für die Kommunikation im Team und die spätere Wartung.
- Die Berücksichtigung nicht-funktionaler Anforderungen wie Performance, Sicherheit und Skalierbarkeit.
- **Abgrenzung & Grenzen:** Systemdesign grenzt sich ab von:
- **Anforderungsanalyse**: Hier werden die *Was*-Fragen geklärt (z. B. [[Use_Case]]s), während Systemdesign die *Wie*-Fragen beantwortet.
- **Implementierung**: Systemdesign trifft keine detaillierten Entscheidungen über Algorithmen oder Datenstrukturen (außer in groben Zügen).
- **Architektur vs. Detaildesign**: Systemdesign kann sich auf die grobe Architektur (z. B. [[Komponentendiagramm]]) oder detailliertere Entwurfsentscheidungen (z. B. [[Klassendiagramm]]) beziehen, wobei die Grenzen fließend sind.

Typische Stolpersteine:
- **Überdesign**: Zu frühe Festlegung auf komplexe Lösungen, bevor die Anforderungen vollständig verstanden sind.
- **Unterschätzung von Schnittstellen**: Unklare oder zu starre [[Schnittstellen]] führen zu Integrationsproblemen.
- **Vernachlässigung nicht-funktionaler Anforderungen**: Performance oder Skalierbarkeit werden erst in der Implementierung berücksichtigt.
- **Fehlende Dokumentation**: Systemdesign-Entscheidungen sind ohne [[UML]]-Diagramme oder textuelle Beschreibungen schwer nachvollziehbar.
- **Beispiel / Code:** ```mermaid
sequenceDiagram
    actor Nutzer
    participant System
    participant Datenbank

    Nutzer->>System: Bestellung aufgeben(artikelId, menge)
    activate System
    System->>Datenbank: prüfeVerfügbarkeit(artikelId)
    Datenbank-->>System: verfügbar: true
    System->>Datenbank: reserviereBestand(artikelId, menge)
    Datenbank-->>System: Reservierung erfolgreich
    System-->>Nutzer: Bestellbestätigung
    deactivate System
```

**Erläuterung**:
- Das [[System-Sequenz-Diagramm]] zeigt die Interaktion zwischen Nutzer, System und Datenbank bei einer Bestellung.
- Die [[Systemgrenze]] umfasst hier das `System` (z. B. ein E-Commerce-Backend), während `Nutzer` und `Datenbank` externe Akteure sind.
- Die [[Schnittstelle]] zwischen System und Datenbank ist durch die Methoden `prüfeVerfügbarkeit` und `reserviereBestand` definiert.
