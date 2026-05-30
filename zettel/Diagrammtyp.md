---
id: ef7b9b4d-6ddc-4901-834c-cbd098f9ed24
title: "Diagrammtyp"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - softwaremodellierung
  - systemanalyse
  - entwurfsmuster
  - diagrammtechniken
  - draft
source: "Klausur_Referenz"
---

# [[Diagrammtyp]]

- **Kernkonzept:** Ein [[Diagrammtyp]] bezeichnet eine standardisierte, visuelle Repräsentationsform zur Modellierung spezifischer Aspekte eines [[Softwaresystems]] oder dessen Entwicklungsprozesses. Diagrammtypen sind in der [[Unified_Modeling_Language_(UML)]] oder anderen Notationen (z. B. [[Entity-Relationship-Diagramm]]) definiert und dienen der Abstraktion, Kommunikation oder Dokumentation von Strukturen, Verhalten oder Interaktionen. Beispiele umfassen [[Klassendiagramm]], [[Sequenzdiagramm]], [[Use-Case-Diagramm]] oder [[Aktivitätsdiagramm]].
- **Nutzen & Zweck:** Diagrammtypen ermöglichen:
1. **Kommunikation**: Vereinfachte Darstellung komplexer Sachverhalte für Stakeholder (z. B. Entwickler, Product Owner).
2. **Analyse & Entwurf**: Frühzeitige Identifikation von Systemanforderungen (z. B. via [[Use-Case-Diagramm]]) oder Architekturentscheidungen (z. B. via [[Komponentendiagramm]]).
3. **Dokumentation**: Langfristige Nachvollziehbarkeit von Systemdesign (z. B. [[Zustandsdiagramm]] für Objektlebenszyklen).
4. **Fehlererkennung**: Visuelle Validierung von Interaktionen (z. B. [[Sequenzdiagramm]] zur Aufdeckung von Deadlocks).

Sie sind essenziell in [[Modellgetriebener_Entwicklung]] und agilen Methoden wie [[Scrum]] (z. B. für Sprint-Planning).
- **Abgrenzung & Grenzen:** 1. **Zweckgebundenheit**: Jeder Diagrammtyp adressiert spezifische Fragestellungen (z. B. [[Sequenzdiagramm]] für zeitliche Abläufe vs. [[Klassendiagramm]] für statische Strukturen). Eine Vermischung führt zu unklaren Modellen.
2. **Abstraktionsebene**: Diagramme sind keine Implementierungsvorlagen (z. B. [[Aktivitätsdiagramm]] vs. konkreter Code).
3. **Toolabhängigkeit**: Manche Typen (z. B. [[Timing_Diagramm]]) erfordern spezielle UML-Tools für präzise Darstellung.
4. **Stolpersteine**: 
   - Überladung (zu viele Details in einem Diagramm).
   - Inkonsistenz zwischen Diagrammen (z. B. widersprüchliche [[Klassendiagramm]]- und [[Sequenzdiagramm]]-Modelle).
   - Vernachlässigung der Zielgruppe (z. B. zu technische [[Zustandsdiagramm]]-Details für Business-Stakeholder).
- **Beispiel / Code:** {'mermaid_sequence': '```mermaid\nsequenceDiagram\n    participant Shop\n    participant Order\n    participant Item\n    Shop->>Order: execute(ord)\n    Order->>Item: getItem()\n    Item-->>Order: x:Item\n    Note right of Order: Attributbindung des Rückgabewerts\n```', 'beschreibung': 'Das Beispiel zeigt ein [[Sequenzdiagramm]] für die Interaktion beim Ausführen einer Bestellung (`execute(ord)`). Es verdeutlicht:\n- **Objektinteraktionen** (Shop → Order → Item).\n- **Zeitliche Abfolge** (vertikale Achse).\n- **Rückgabewerte** (Item an Order).\n\nVergleichbar wäre ein [[Aktivitätsdiagramm]] für denselben Use Case, das jedoch den Workflow (z. B. mit [[Swimlanes]]) statt der Objektkommunikation betont.'}
