---
id: 6e14f19c-f2b6-4cd5-bec8-9f2c7353640f
title: "Nicht_funktionale_Anforderung"
date: 2026-05-31
tags:
  - software_engineering
  - anforderungsanalyse
  - softwarearchitektur
  - qualitaetssicherung
  - metriken
  - iso_25010
  - draft
source: "Klausur_Referenz"
---

# [[Nicht_funktionale_Anforderung]]

- **Kernkonzept:** Nicht-funktionale Anforderungen (NFA) definieren Qualitätsmerkmale und Rahmenbedingungen eines [[Softwaresystems]], die nicht direkt die funktionalen Aspekte (z. B. spezifische Features oder Geschäftslogik) betreffen, sondern vielmehr die Art und Weise, wie diese Funktionen bereitgestellt werden. Sie sind subjektiv und kontextabhängig, da sie sich auf Eigenschaften wie Performance, Sicherheit, Benutzerfreundlichkeit oder Wartbarkeit beziehen. Um sie operationalisierbar zu machen, werden sie durch [[Metriken]] quantifiziert, z. B. "Die Antwortzeit darf 2 Sekunden nicht überschreiten".
- **Nutzen & Zweck:** Nicht-funktionale Anforderungen dienen dazu, die Qualität und Akzeptanz eines [[Softwaresystems]] sicherzustellen, indem sie nicht-funktionale Aspekte wie Skalierbarkeit, Zuverlässigkeit oder Compliance explizit machen. Sie sind entscheidend für die [[Softwarearchitektur]], da sie die Wahl von [[Entwurfsmustern]] (z. B. [[CQRS]] für Performance) oder Technologien (z. B. Datenbanken für Skalierbarkeit) beeinflussen. Zudem ermöglichen sie eine objektive Bewertung der Systemqualität durch messbare Kriterien, was für die [[Qualitätssicherung]] und [[Risikomanagement]] essenziell ist.
- **Abgrenzung & Grenzen:** Nicht-funktionale Anforderungen unterscheiden sich von [[funktionalen_Anforderungen]] dadurch, dass letztere konkrete Funktionen oder Verhalten des Systems beschreiben (z. B. "Das System muss Bestellungen speichern"), während NFA Eigenschaften des Systems oder dessen Betrieb betreffen. Typische Stolpersteine sind:
- **Subjektivität**: Ohne klare [[Metriken]] sind NFA schwer verhandelbar (z. B. "Das System soll benutzerfreundlich sein").
- **Konflikte**: NFA können sich widersprechen (z. B. hohe Sicherheit vs. hohe Performance).
- **Implizite Annahmen**: NFA werden oft als selbstverständlich vorausgesetzt (z. B. Verfügbarkeit) und erst spät im Projekt thematisiert.
- **Messbarkeit**: Nicht alle NFA lassen sich einfach quantifizieren (z. B. Wartbarkeit). Hier helfen [[Qualitätsmodelle]] wie ISO 25010.
- **Beispiel / Code:** ```mermaid
classDiagram
    class System {
        +funktionaleAnforderungen()
        +nichtFunktionaleAnforderungen()
    }
    class NichtFunktionaleAnforderung {
        <<interface>>
        +metrikDefinieren()
        +grenzwertFestlegen()
    }
    class Performance {
        +antwortzeit: Zeit
        +durchsatz: Anfragen/Sekunde
        +metrikDefinieren()
    }
    class Sicherheit {
        +verschluesselung: Algorithmus
        +authentifizierung: Methode
        +metrikDefinieren()
    }
    System --> NichtFunktionaleAnforderung
    NichtFunktionaleAnforderung <|-- Performance
    NichtFunktionaleAnforderung <|-- Sicherheit
```

**Beispiel (textuell):**
- **NFA**: "Das System muss 99,9% der Zeit verfügbar sein."
- **Metrik**: Verfügbarkeit = (Gesamtzeit - Ausfallzeit) / Gesamtzeit * 100.
- **Grenzwert**: ≥ 99,9%.
- **Umsetzung**: Einsatz von [[Redundanz]] und [[Load_Balancing]].
