---
id: 2b3d3e77-b272-40d5-8a6f-81d1a171c7e2
title: "Backlog"
date: 2026-05-30
tags:
  - software_engineering
  - agile_entwicklung
  - scrum
  - anforderungsmanagement
  - projektmanagement
  - user_stories
  - draft
source: "Klausur_Referenz"
---

# [[Backlog]]

- **Kernkonzept:** Ein **Backlog** ist eine priorisierte Liste von Anforderungen, Aufgaben oder Arbeitspaketen in der agilen Softwareentwicklung, insbesondere in [[Scrum]]. Es dient als zentrale Quelle für alle geplanten und umzusetzenden Elemente eines Projekts. Man unterscheidet zwischen dem **Product_Backlog** (gesamte Anforderungen an das Produkt) und dem **Sprint_Backlog** (Aufgaben für den aktuellen [[Sprint]]). Der Backlog ist dynamisch und wird kontinuierlich durch [[Backlog_Refinement]] (auch *Grooming* genannt) angepasst und verfeinert.
- **Nutzen & Zweck:** Der Backlog erfüllt mehrere zentrale Zwecke:
- **Transparenz**: Alle Stakeholder haben eine klare Übersicht über den Projektumfang und den Fortschritt.
- **Priorisierung**: Anforderungen werden nach Geschäftswert, Risiko oder Abhängigkeiten geordnet (z. B. mittels [[MoSCoW_Methode]]).
- **Flexibilität**: Durch regelmäßige Anpassung (z. B. in [[Sprint_Planning]]) kann auf Änderungen reagiert werden.
- **Arbeitssteuerung**: Das Entwicklungsteam zieht Aufgaben aus dem **Sprint_Backlog** und setzt sie um, während der **Product_Backlog** langfristige Planung ermöglicht.
- **Kommunikation**: Dient als Grundlage für Diskussionen zwischen Product_Owner, Scrum_Master und Entwicklungsteam.
- **Abgrenzung & Grenzen:** 1. **Product_Backlog vs. Sprint_Backlog**: 
   - Der **Product_Backlog** ist eine lebende Liste *aller* bekannten Anforderungen (z. B. Features, Bugfixes, technische Schulden) und gehört dem [[Product_Owner]].
   - Der **Sprint_Backlog** ist eine Teilmenge des Product_Backlogs, die für einen [[Sprint]] ausgewählt und in konkrete [[User_Stories]] oder Tasks heruntergebrochen wird. Er gehört dem Entwicklungsteam.
2. **Stolpersteine**:
   - **Überladung**: Ein zu detaillierter oder zu großer Backlog führt zu Unübersichtlichkeit. Lösung: Regelmäßiges [[Backlog_Refinement]].
   - **Statische Priorisierung**: Backlogs müssen dynamisch bleiben – starre Prioritäten behindern Agilität.
   - **Fehlende Akzeptanzkriterien**: Unklare [[Definition_of_Done]] führt zu Missverständnissen.
   - **Technische Schulden**: Werden oft vernachlässigt, sollten aber explizit im Backlog aufgeführt werden.
3. **Abgrenzung zu anderen Konzepten**:
   - Kein [[Wasserfallmodell]]: Backlogs sind *keine* festen Spezifikationen, sondern passen sich an.
   - Kein [[Kanban_Board]]: Während ein Kanban-Board den *Workflow* visualisiert, ist der Backlog eine *priorisierte Liste* – beide können aber kombiniert werden (z. B. in [[Scrumban]]).
- **Beispiel / Code:** ```mermaid
classDiagram
    class ProductBacklog {
        +List~BacklogItem~ items
        +priorisiere()
        +verfeinere()
    }
    class SprintBacklog {
        +List~Task~ tasks
        +zieheAufgabe()
        +aktualisiereFortschritt()
    }
    class BacklogItem {
        <<abstract>>
        +String beschreibung
        +int prioritaet
        +String akzeptanzkriterien
    }
    class UserStory {
        +String als
        +String moechteIch
        +String damit
    }
    class Task {
        +String beschreibung
        +String zustand
        +int aufwand
    }

    ProductBacklog "1" *-- "0..*" BacklogItem
    SprintBacklog "1" *-- "0..*" Task
    BacklogItem <|-- UserStory
```

**Beispiel für eine User Story im Product Backlog (als Text):**
```
Als [Registrierter_Nutzer]
Möchte ich [mein Passwort zurücksetzen können]
Damit [ich wieder Zugang zu meinem Konto erhalte, falls ich es vergesse].

Akzeptanzkriterien:
- Link zum Zurücksetzen wird per E-Mail versendet.
- Passwort muss mindestens 8 Zeichen enthalten.
- Link ist nur 24 Stunden gültig.
```
