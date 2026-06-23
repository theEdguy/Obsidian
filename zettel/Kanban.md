---
id: 5c0e8e12-7b62-4b38-b893-5e8ae91d2a7e
title: "Kanban"
date: 2026-06-23
tags:
  - software_engineering
  - agile_methoden
  - prozessmodell
  - workflow_management
  - lean
  - visualisierung
  - prozess
  - projektmanagement
  - agil
  - draft
source: "software_engineering_kapitel_12"
---

# [[Kanban]]

- **Kernkonzept:** Kanban ist eine [[agile_Methode|agile Methode]] zur [[Prozessmodell|Prozesssteuerung]] und -verbesserung, die ursprünglich aus der [[Lean_Production|Lean-Produktion]] stammt und auf visuelle [[Workflow_Management|Arbeitsorganisation]] setzt. Im [[Software_Engineering]] dient Kanban dazu, den [[Workflow]] zu visualisieren, die Arbeitslast durch [[Work-in-Progress-Limit|Work-in-Progress-Limits (WIP)]] zu begrenzen und kontinuierliche Lieferung zu ermöglichen, ohne feste [[Iteration|Iterationen]] wie bei [[Scrum]] vorzugeben.
- **Nutzen & Zweck:** Kanban löst Probleme wie unklare Arbeitsabläufe, Teamüberlastung und ineffiziente Priorisierung, indem es Transparenz über den Fortschritt von [[Aufgabe|Aufgaben]] schafft und [[Engpass|Engpässe]] sichtbar macht. Durch WIP-Limits wird [[Multitasking]] reduziert, was die Effizienz steigert und kontinuierliche Auslieferung (z. B. in [[Continuous_Delivery|Continuous-Delivery-Pipelines]]) ermöglicht. Besonders nützlich ist Kanban in dynamischen Umgebungen mit variierenden Arbeitslasten, wie Wartungsteams oder Projekten mit unvorhersehbaren Anforderungen. Es fördert [[Kaizen|kontinuierliche Verbesserung]] durch Flussoptimierung und flexible Anpassung an Veränderungen, ohne starre Strukturen wie [[Sprint|Sprints]] oder vordefinierte [[Rolle|Rollen]]. Typische Anwendungsfälle umfassen:

- **Visualisierung des Workflows**: [[Aufgabe|Aufgaben]] werden auf einem Kanban-Board mit Spalten wie *To Do*, *In Progress*, *Review* und *Done* dargestellt, um den Fortschritt für alle [[Team|Teammitglieder]] transparent zu machen.
- **Begrenzung paralleler Arbeit**: WIP-Limits verhindern Überlastung und stellen sicher, dass [[Aufgabe|Aufgaben]] abgeschlossen werden, bevor neue begonnen werden.
- **Kontinuierliche Auslieferung**: Fertige [[Aufgabe|Aufgaben]] können jederzeit ausgeliefert werden, was die Integration in [[DevOps]]-Prozesse erleichtert.
- **Flexibilität**: Kanban eignet sich für Teams mit unvorhersehbaren Arbeitslasten, da es keine festen Iterationen erfordert und sich leicht in bestehende Prozesse integrieren lässt.

Vorteile gegenüber anderen [[agile_Methode|agilen Methoden]] wie [[Scrum]] sind die geringere Formalisierung und die Anpassbarkeit an bestehende [[Prozessmodell|Prozessmodelle]], was besonders in [[Wartung|Wartungsprojekten]] oder bei der Kombination mit [[Scrumban]] (Hybrid aus Scrum und Kanban) zum Tragen kommt.
- **Abgrenzung & Grenzen:** Kanban ist **kein Projektmanagement-Framework** im engeren Sinne, sondern ein Werkzeug zur [[Prozessoptimierung]]. Es eignet sich weniger für Projekte mit klar definierten, langfristigen [[Meilenstein|Meilensteinen]] oder stark regulierten Umgebungen, die detaillierte Vorabplanung erfordern (z. B. [[Wasserfallmodell]]). Typische Grenzen und Stolpersteine sind:

- **Fehlende Zeitvorgaben**: Ohne feste [[Iteration|Iterationen]] oder [[Sprint|Sprints]] kann die Planung bei Projekten mit klaren Deadlines schwieriger sein, da keine Zeitboxen wie bei [[Scrum]] vorgegeben sind.
- **Überlastung durch WIP-Limits**: Werden WIP-Limits ignoriert, verliert Kanban seine Wirksamkeit, z. B. wenn [[Aufgabe|Aufgaben]] blockiert werden, um neue zu starten, was zu [[Technische_Schuld|technischer Schuld]] führen kann.
- **Keine vordefinierten Rollen oder Meetings**: Im Gegensatz zu [[Scrum]] gibt es keine festen [[Rolle|Rollen]] (z. B. [[Scrum_Master]]) oder Events (z. B. [[Retrospektive|Retrospektiven]]), was bei unerfahrenen Teams zu mangelnder Struktur oder fehlender Reflexion führen kann.
- **Abhängigkeit von Disziplin**: Kanban erfordert hohe Selbstorganisation und kontinuierliche Reflexion, um Verbesserungen umzusetzen. Ohne regelmäßige [[Prozessanalyse]] kann der [[Workflow]] stagnieren.
- **Nicht für alle Projekte geeignet**: Bei stark sequenziellen oder phasenbasierten Projekten (z. B. [[Wasserfallmodell]]) ist Kanban weniger passend, da es auf kontinuierlichen Fluss und flexible Priorisierung setzt. Alternativen wie [[Scrum]] oder [[Extreme_Programming]] bieten hier mehr Struktur.

Kanban wird oft mit [[Scrum]] kombiniert (Scrumban), um die Vorteile beider Ansätze zu nutzen, z. B. durch die Einführung von WIP-Limits in [[Sprint|Sprints]] oder die Beibehaltung von [[Daily_Stand-up|Daily Stand-ups]] ohne feste Iterationen.
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
        +Zugewiesen: Teammitglied
    }
    
    KanbanBoard "1" *-- "1..*" Spalte
    Spalte "1" *-- "0..*" Aufgabe
    
    note for KanbanBoard "Beispiel-Spalten mit WIP-Limits:\n- To Do (WIP: ∞)\n- In Progress (WIP: 3)\n- Review (WIP: 2)\n- Done (WIP: ∞)"
```

```java
// Beispiel für eine einfache Kanban-Board-Klasse in Java mit WIP-Limit-Logik
import java.util.ArrayList;
import java.util.List;

public class KanbanBoard {
    private List<String> todo;
    private List<String> inProgress;
    private List<String> review;
    private List<String> done;
    private final int wipLimitInProgress = 3;
    private final int wipLimitReview = 2;

    public KanbanBoard() {
        this.todo = new ArrayList<>();
        this.inProgress = new ArrayList<>();
        this.review = new ArrayList<>();
        this.done = new ArrayList<>();
    }

    public void addTask(String task) {
        todo.add(task);
        System.out.println("[[Aufgabe]] hinzugefügt: " + task);
    }

    public void moveToInProgress(String task) {
        if (inProgress.size() < wipLimitInProgress && todo.remove(task)) {
            inProgress.add(task);
            System.out.println("[[Aufgabe]] in Arbeit verschoben: " + task);
        } else {
            System.out.println("Fehler: WIP-Limit erreicht oder [[Aufgabe]] nicht gefunden.");
        }
    }

    public void moveToReview(String task) {
        if (review.size() < wipLimitReview && inProgress.remove(task)) {
            review.add(task);
            System.out.println("[[Aufgabe]] in Review verschoben: " + task);
        } else {
            System.out.println("Fehler: WIP-Limit erreicht oder [[Aufgabe]] nicht gefunden.");
        }
    }

    public void moveToDone(String task) {
        if (review.remove(task)) {
            done.add(task);
            System.out.println("[[Aufgabe]] abgeschlossen: " + task);
        } else {
            System.out.println("Fehler: [[Aufgabe]] nicht in Review gefunden.");
        }
    }
}
```

**Textuelle Beschreibung eines Kanban-Boards (Beispiel mit WIP-Limits und Blockaden):**
| To Do               | In Progress (WIP: 3/3)       | Review (WIP: 2/2)       | Done               |
|---------------------|----------------------------|-----------------------|--------------------|
| Feature A implementieren | API-Anbindung (Max)       | UI-Tests (Anna)       | Datenbank-Migration |
| Bug #123 fixen       | Dokumentation (Lisa)      | Code-Review (Tom)     |                    |
| [[Refactoring]] [[Observer_Pattern|Observer-Pattern]] | **Blockiert: Wartend auf Backend** |                       |                    |

*Hinweis: Die [[Aufgabe]] "[[Refactoring]] [[Observer_Pattern|Observer-Pattern]]" ist blockiert, da das WIP-Limit in *In Progress* erreicht ist. Erst nach Abschluss einer [[Aufgabe]] kann eine neue begonnen werden.*

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5a2
- **Vorgänger / Parent:** [[Agile_Methoden]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Iterative_Entwicklung]]
  - [[Agile_Methoden]]
