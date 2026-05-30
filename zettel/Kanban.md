---
id: 0a612b94-0161-4464-b48f-4739e7651637
title: "Kanban"
date: 2026-05-30
tags:
  - software_engineering
  - agile_methoden
  - prozessmodell
  - workflow_management
  - lean
  - visualisierung
  - draft
source: "Klausur_Referenz"
---

# [[Kanban]]

- **Kernkonzept:** Kanban ist eine agile Methode zur Prozesssteuerung und -verbesserung, die ursprünglich aus der Lean-Produktion stammt und auf visuelle Arbeitsorganisation setzt. Im Software-Engineering dient Kanban dazu, den Workflow zu visualisieren, die Arbeitslast zu begrenzen (Work-in-Progress-Limits, WIP) und kontinuierliche Lieferung zu ermöglichen. Im Gegensatz zu [[Scrum]] gibt es keine festen Iterationen (Sprints), sondern einen kontinuierlichen Fluss von Aufgaben, die nach Priorität abgearbeitet werden. Kernprinzipien sind Transparenz, Flussoptimierung und kontinuierliche Verbesserung (Kaizen).
- **Nutzen & Zweck:** Kanban wird eingesetzt, um Engpässe im Entwicklungsprozess sichtbar zu machen, die Effizienz zu steigern und die Liefergeschwindigkeit zu erhöhen. Typische Anwendungsfälle sind:
- **Visualisierung des Workflows**: Aufgaben werden auf einem Kanban-Board (z. B. mit Spalten wie *To Do*, *In Progress*, *Review*, *Done*) dargestellt, um den Fortschritt für alle Teammitglieder transparent zu machen.
- **Begrenzung der parallelen Arbeit**: Durch WIP-Limits wird verhindert, dass Teams überlastet werden und Aufgaben unvollendet bleiben.
- **Kontinuierliche Auslieferung**: Da keine festen Sprints existieren, können fertige Aufgaben jederzeit ausgeliefert werden (z. B. in [[Continuous_Delivery]]-Pipelines).
- **Flexibilität**: Kanban eignet sich besonders für Teams mit unvorhersehbaren oder variierenden Arbeitslasten (z. B. Wartungsteams).

Vorteile gegenüber anderen agilen Methoden wie [[Scrum]] sind die geringere Formalisierung und die Anpassbarkeit an bestehende Prozesse.
- **Abgrenzung & Grenzen:** Kanban ist **kein Projektmanagement-Framework** im engeren Sinne, sondern ein Werkzeug zur Prozessoptimierung. Typische Grenzen und Stolpersteine sind:
- **Fehlende Zeitvorgaben**: Ohne feste Iterationen kann die Planung schwieriger sein, besonders bei Projekten mit klaren Deadlines.
- **Überlastung durch WIP-Limits**: Werden Limits ignoriert, verliert Kanban seine Wirksamkeit (z. B. wenn Aufgaben „blockiert“ werden, um neue zu starten).
- **Keine Rollen oder Meetings**: Im Gegensatz zu [[Scrum]] gibt es keine vordefinierten Rollen (z. B. Scrum Master) oder Events (z. B. Retrospektiven), was zu mangelnder Struktur führen kann.
- **Abhängigkeit von Disziplin**: Kanban erfordert Selbstorganisation und kontinuierliche Reflexion, um Verbesserungen umzusetzen.
- **Nicht für alle Projekte geeignet**: Bei stark sequenziellen oder phasenbasierten Projekten (z. B. Wasserfall) ist Kanban weniger passend.

Kanban wird oft mit [[Scrum]] kombiniert (Scrumban), um die Vorteile beider Ansätze zu nutzen.
- **Beispiel / Code:** ```mermaid
classDiagram
    class KanbanBoard {
        +Spalten: List~Spalte~
        +addSpalte(spalte: Spalte)
        +moveAufgabe(aufgabe: Aufgabe, zielSpalte: Spalte)
    }
    
    class Spalte {
        +Name: String
        +WIPLimit: int
        +Aufgaben: List~Aufgabe~
        +addAufgabe(aufgabe: Aufgabe)
        +removeAufgabe(aufgabe: Aufgabe)
    }
    
    class Aufgabe {
        +Titel: String
        +Beschreibung: String
        +Priorität: int
        +Status: String
    }
    
    KanbanBoard "1" *-- "1..*" Spalte
    Spalte "1" *-- "0..*" Aufgabe

    note for KanbanBoard "Beispiel-Spalten:\n- To Do\n- In Progress (WIP-Limit: 3)\n- Review\n- Done"
```

**Textuelle Beschreibung eines Kanban-Boards (Beispiel):**
| To Do               | In Progress (WIP: 3/3) | Review          | Done               |
|---------------------|-----------------------|------------------|--------------------|
| Feature A implementieren | API-Anbindung (Max)   | UI-Tests (Anna)  | Datenbank-Migration |
| Bug #123 fixen       | Dokumentation (Lisa)  | Code-Review (Tom)|                    |
| Refactoring [[Observer_Pattern]] |                     |                  |                    |
