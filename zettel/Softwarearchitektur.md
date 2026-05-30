---
id: 69b2d74e-4a48-421f-b97c-292b0340ea28
title: "Softwarearchitektur"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - entwurfsmuster
  - uml
  - schichtenarchitektur
  - nicht-funktionale_anforderungen
  - modularisierung
  - systemdesign
  - draft
source: "Klausur_Referenz"
---

# [[Softwarearchitektur]]

- **Kernkonzept:** Softwarearchitektur bezeichnet die grundlegende Struktur eines Softwaresystems, die durch die Definition von [[Komponenten]], [[Konnektoren]], [[Modulen]] und deren Beziehungen zueinander entsteht. Sie legt fest, wie das System in logische und physische Einheiten unterteilt wird, um funktionale und nicht-funktionale Anforderungen (z. B. [[Skalierbarkeit]], [[Wartbarkeit]], [[Sicherheit]]) zu erfüllen. Die Architektur dient als Blaupause für die Implementierung und ermöglicht die Kommunikation zwischen Stakeholdern über technische und konzeptionelle Entscheidungen.
- **Nutzen & Zweck:** 1. **Strukturierung**: Schafft Klarheit über die Systemkomponenten und deren Interaktionen, z. B. durch [[Schichtenarchitektur]] oder [[Microservices]].
2. **Risikominimierung**: Frühzeitige Identifikation von Konflikten (z. B. bei [[Performance]] oder [[Datenkonsistenz]]) durch Modellierung.
3. **Wiederverwendbarkeit**: Förderung von [[Entwurfsmustern]] (z. B. [[Facade_Pattern]]) und modularen Designs.
4. **Kommunikation**: Ermöglicht die Abstimmung zwischen Entwicklern, Architekten und nicht-technischen Stakeholdern (z. B. via [[UML]]-Diagramme wie [[Komponentendiagramm]] oder [[Sequenzdiagramm]]).
5. **Anpassungsfähigkeit**: Erleichtert die Evolution des Systems durch klare [[Schnittstellen]] und lose Kopplung (vgl. [[Dependency_Inversion_Principle]]).
- **Abgrenzung & Grenzen:** 1. **Kein Detaildesign**: Die Architektur definiert *was* und *warum*, nicht *wie* im Kleinen (z. B. Algorithmen oder konkrete Klassenimplementierungen).
2. **Kein Code**: Sie ist abstrakt und wird erst durch [[Implementierungsmodelle]] (z. B. [[Klassendiagramm]]) konkretisiert.
3. **Stolpersteine**: 
   - **Über-Engineering**: Zu frühe Festlegung auf komplexe Muster (z. B. [[Event_Driven_Architecture]]) ohne Notwendigkeit.
   - **Technische Schulden**: Vernachlässigung von [[Qualitätsattributen]] (z. B. [[Testbarkeit]]) zugunsten schneller Lösungen.
   - **Stakeholder-Konflikte**: Unterschiedliche Prioritäten (z. B. [[Kosten]] vs. [[Flexibilität]]) erfordern Kompromisse.
4. **KI-Einfluss**: Automatisierte Architekturgenerierung (z. B. durch [[Large_Language_Models]]) kann Entwürfe beschleunigen, ersetzt aber keine menschliche Validierung von [[Nicht-funktionale_Anforderungen]].
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer vereinfachten [[Schichtenarchitektur]] für ein E-Commerce-System (textuelle UML-Notation im Stil von Mermaid):', 'mermaid_diagramm': 'classDiagram\n    direction TB\n    class PresentationLayer {\n        +showProductList()\n        +processCheckout()\n    }\n    class BusinessLogicLayer {\n        +calculatePrice()\n        +validateOrder()\n    }\n    class DataAccessLayer {\n        +saveOrder()\n        +loadProductData()\n    }\n    class Database {\n        +executeQuery()\n    }\n\n    PresentationLayer --> BusinessLogicLayer : nutzt\n    BusinessLogicLayer --> DataAccessLayer : nutzt\n    DataAccessLayer --> Database : greift zu\n\n    note for PresentationLayer "UI-Komponenten (z. B. Web-Frontend)"\n    note for BusinessLogicLayer "Geschäftsregeln (z. B. Rabattberechnung)"\n    note for DataAccessLayer "[[Repository_Pattern]] für Datenbankzugriffe"'}
