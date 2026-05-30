---
id: 6c3bee84-827a-49af-81f4-87fc311162f7
title: "Agile_Manifest"
date: 2026-05-30
tags:
  - software_engineering
  - vorgehensmodelle
  - scrum
  - kanban
  - iterative_entwicklung
  - softwareprozess
  - change_management
  - produktmanagement
  - draft
source: "Klausur_Referenz"
---

# [[Agile_Manifest]]

- **Kernkonzept:** Das [[Agile_Manifest]] (engl. *Agile Manifesto*) ist ein grundlegendes Dokument, das 2001 von 17 Softwareentwicklern veröffentlicht wurde, um die Prinzipien agiler Softwareentwicklung zu definieren. Es priorisiert vier zentrale Werte: 1) **Individuen und Interaktionen** über Prozesse und Werkzeuge, 2) **funktionierende Software** über umfassende Dokumentation, 3) **Zusammenarbeit mit dem Kunden** über Vertragsverhandlungen, 4) **Reagieren auf Veränderung** über das Befolgen eines Plans. Diese Werte werden durch zwölf Prinzipien konkretisiert, die iterative Entwicklung, kontinuierliche Lieferung, Selbstorganisation von Teams und adaptive Planung betonen. Das Manifest grenzt sich bewusst von klassischen [[Vorgehensmodelle]]n wie dem [[Wasserfallmodell]] ab, indem es Flexibilität und Kundenorientierung in den Vordergrund stellt.
- **Nutzen & Zweck:** Das [[Agile_Manifest]] dient als philosophische Grundlage für agile Methoden wie [[Scrum]], [[Kanban]] oder [[Extreme_Programming]]. Sein Zweck ist es, Softwareentwicklung effizienter, anpassungsfähiger und nutzerzentrierter zu gestalten. Vorteile umfassen: 
- **Schnellere Wertschöpfung**: Durch iterative [[Sprints]] oder kontinuierliche Auslieferung (z. B. [[Continuous_Delivery]]) werden frühzeitig funktionierende Ergebnisse geliefert.
- **Risikominimierung**: Regelmäßiges Feedback (z. B. durch [[User_Stories]] oder [[Retrospektiven]]) reduziert Fehlentwicklungen.
- **Kundenintegration**: Direkte Zusammenarbeit mit Stakeholdern (z. B. via [[Product_Owner]]) stellt sicher, dass das Produkt den Anforderungen entspricht.
- **Teamautonomie**: Selbstorganisierte Teams fördern Kreativität und Eigenverantwortung.

Das Manifest wird nicht nur in der Softwareentwicklung, sondern auch in anderen Bereichen wie Produktmanagement oder Marketing adaptiert.
- **Abgrenzung & Grenzen:** Das [[Agile_Manifest]] ist **kein konkretes Vorgehensmodell**, sondern ein Werte- und Prinzipienrahmen. Es grenzt sich ab von:
- **Dokumentenlastigen Ansätzen**: Während klassische Modelle (z. B. [[V-Modell]]) detaillierte Spezifikationen fordern, setzt Agilität auf minimale, aber ausreichende Dokumentation (z. B. [[Definition_of_Done]]).
- **Starren Plänen**: Im Gegensatz zum [[Wasserfallmodell]] akzeptiert Agilität Änderungen auch in späten Phasen (vgl. [[Change_Management]]).
- **Hierarchischen Strukturen**: Agile Teams arbeiten selbstorganisiert, was traditionelle Top-down-Steuerung infrage stellt.

**Stolpersteine**: 
- **Fehlinterpretation als „keine Planung“**: Agilität bedeutet nicht Chaos, sondern adaptive Planung (z. B. [[Backlog_Refinement]]).
- **Überbetonung von Tools**: Der Fokus auf Individuen und Interaktionen wird oft durch übermäßigen Einsatz von [[Jira]] oder [[Confluence]] konterkariert.
- **Skalierungsprobleme**: Bei großen Projekten (z. B. [[SAFe]]) können agile Prinzipien durch zusätzliche Prozesse verwässert werden.
- **Kulturelle Hürden**: Agilität erfordert eine offene Fehlerkultur und Vertrauen, was in traditionellen Organisationen schwer umsetzbar ist.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Mermaid-Diagramm veranschaulicht den iterativen Charakter agiler Entwicklung im Vergleich zum linearen [[Wasserfallmodell]]:\n\n```mermaid\nflowchart TD\n    subgraph Wasserfallmodell\n        A[Anforderungen] --> B[Design] --> C[Implementierung] --> D[Test] --> E[Wartung]\n    end\n    subgraph Agile_Entwicklung\n        F[Sprint 1] --> G[Sprint 2] --> H[Sprint 3] --> I[...]\n        F -->|Feedback| F\n        G -->|Feedback| G\n        H -->|Feedback| H\n    end\n```\n\n**Beispiel für ein agiles Prinzip in der Praxis (Scrum):**\nEin [[Scrum_Team]] plant einen 2-wöchigen Sprint mit folgenden [[User_Stories]]:\n1. Als Nutzer möchte ich mich registrieren können (Priorität: Hoch).\n2. Als Admin möchte ich Nutzerdaten exportieren (Priorität: Mittel).\n\nNach dem Sprint wird die funktionierende Software (z. B. ein [[MVP]]) dem Kunden präsentiert, der Feedback gibt. Basierend darauf wird der [[Product_Backlog]] angepasst – ein klassisches Beispiel für „Reagieren auf Veränderung“.', 'code': None}
