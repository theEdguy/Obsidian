---
id: 74ed3602-1963-4315-b741-09b082dcb1c1
title: "Agile_Softwareentwicklung"
date: 2026-05-30
tags:
  - software_engineering
  - softwareentwicklungsprozess
  - iterative_entwicklung
  - scrum
  - kanban
  - risikomanagement
  - user_stories
  - sprints
  - retrospektive
  - spiralmodell
  - draft
source: "Klausur_Referenz"
---

# [[Agile_Softwareentwicklung]]

- **Kernkonzept:** Agile_Softwareentwicklung ist ein iterativer und inkrementeller Ansatz zur Entwicklung von Software, der auf Flexibilität, Kundenzentrierung und kontinuierliche Verbesserung setzt. Sie basiert auf dem [[Spiralmodell]] von Boehm (1988) und betont die frühzeitige Identifikation und Bewältigung von Risiken. Im Gegensatz zu traditionellen [[Wasserfallmodell]]-Ansätzen wird das Projekt in kleine, überschaubare Einheiten (z. B. [[Sprints]] im [[Scrum]]) zerlegt, die regelmäßig evaluiert und angepasst werden. Neue Anforderungen können während des gesamten Entwicklungsprozesses integriert werden, was eine dynamische Reaktion auf Veränderungen ermöglicht.
- **Nutzen & Zweck:** Agile_Softwareentwicklung dient der effizienten und kundenorientierten Umsetzung von Softwareprojekten, insbesondere in dynamischen Umgebungen mit unklaren oder sich ändernden Anforderungen. Zu den Vorteilen zählen:
- **Frühzeitige Lieferung funktionsfähiger Software**: Durch iterative Entwicklung können Teilprodukte bereits frühzeitig eingesetzt und getestet werden.
- **Kundenzufriedenheit**: Regelmäßige Feedbackschleifen mit dem Kunden (z. B. durch [[User_Stories]] oder [[Product_Backlog]]) stellen sicher, dass das Endprodukt den Anforderungen entspricht.
- **Risikominimierung**: Durch kontinuierliche Evaluation und Anpassung (z. B. im [[Retrospektive]]-Meeting) werden Risiken früh erkannt und behoben.
- **Transparenz und Zusammenarbeit**: Agile Methoden fördern die Selbstorganisation von Teams (z. B. durch [[Daily_Standup]]) und eine offene Kommunikation.
- **Anpassungsfähigkeit**: Änderungen in den Anforderungen oder Rahmenbedingungen können flexibel berücksichtigt werden, ohne den gesamten Projektplan zu gefährden.
- **Abgrenzung & Grenzen:** Agile_Softwareentwicklung grenzt sich von starren, sequenziellen Modellen wie dem [[Wasserfallmodell]] ab, die eine vollständige Planung zu Projektbeginn voraussetzen. Allerdings hat auch Agilität Grenzen und typische Stolpersteine:
- **Nicht für alle Projekte geeignet**: Projekte mit klar definierten, stabilen Anforderungen (z. B. sicherheitskritische Systeme) profitieren möglicherweise weniger von Agilität.
- **Dokumentation**: Agile Methoden legen weniger Wert auf umfangreiche Vorabdokumentation, was zu Wissensverlust führen kann, wenn Teammitglieder wechseln.
- **Kundenbeteiligung**: Agile Prozesse erfordern eine aktive und kontinuierliche Einbindung des Kunden, was in der Praxis oft schwer umsetzbar ist.
- **Skalierung**: Agile Methoden wie [[Scrum]] oder [[Kanban]] sind für kleine Teams optimiert. Bei großen Projekten mit vielen Teams (z. B. [[SAFe]]) steigt die Komplexität.
- **Kulturelle Hürden**: Agile Prinzipien erfordern eine offene Fehlerkultur und Selbstorganisation, was in hierarchischen Organisationen auf Widerstand stoßen kann.
- **Messbarkeit**: Traditionelle Metriken (z. B. Meilensteine) sind in agilen Projekten schwerer anwendbar, was die Fortschrittskontrolle erschwert.
- **Beispiel / Code:** ```mermaid
flowchart TD
    A[Projektstart] --> B[Planung: Ziele & Risiken identifizieren]
    B --> C[Entwicklung: Sprint 1]
    C --> D[Review: Ergebnis präsentieren & Feedback einholen]
    D --> E[Retrospektive: Prozess verbessern]
    E --> F{Risiken behoben?}
    F -->|Nein| B
    F -->|Ja| G[Entwicklung: Sprint 2]
    G --> D
    D -->|Projektende| H[Auslieferung]
```

**Beispiel für eine [[User_Story]] im [[Product_Backlog]]:**
```plaintext
Als [Nutzer] möchte ich [meine Aufgaben priorisieren können], damit [ich meine Arbeit effizienter erledigen kann].
Akzeptanzkriterien:
- Aufgaben können per Drag & Drop sortiert werden.
- Prioritäten werden in der Datenbank gespeichert.
- Änderungen sind für alle Teammitglieder sichtbar.
```
