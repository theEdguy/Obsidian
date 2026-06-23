---
id: 638aa9cb-d3ab-435f-bb40-4bae1181f942
title: "Sprint Planning"
date: 2026-06-23
tags:
  - software_engineering
  - sprint_planning
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Sprint Planning]]

- **Kernkonzept:** Sprint Planning ist ein zentrales Ereignis im Scrum-Framework, bei dem das Entwicklungsteam gemeinsam mit dem Product Owner die Ziele und Aufgaben für den kommenden Sprint festlegt. Dabei werden die priorisierten Product Backlog-Einträge in konkrete Sprint Backlog-Items überführt und deren Umsetzung geplant.
- **Nutzen & Zweck:** Sprint Planning existiert, um Klarheit über die anstehenden Arbeitsaufgaben zu schaffen und sicherzustellen, dass das Team realistische Ziele für den Sprint setzt. Es löst das Problem unklarer Prioritäten, fehlender Abstimmung zwischen Stakeholdern und Entwicklern sowie unstrukturierter Arbeitsplanung, indem es Transparenz, Fokus und Commitment für die Sprint-Ziele schafft. Zudem ermöglicht es eine frühzeitige Risikoeinschätzung und Ressourcenplanung.
- **Abgrenzung & Grenzen:** Sprint Planning sollte nicht genutzt werden, wenn das Product Backlog unzureichend vorbereitet oder priorisiert ist, da dies zu unrealistischen Planungen führt. Es unterscheidet sich von klassischen Projektplanungsmethoden wie dem Wasserfallmodell, da es iterativ und flexibel ist und keine starren Langzeitpläne vorgibt. Alternativen wie Kanban verzichten vollständig auf feste Planungsphasen und setzen stattdessen auf kontinuierlichen Workflow. Sprint Planning ist zudem ungeeignet für Projekte mit extrem unklaren Anforderungen oder wenn das Team keine Selbstorganisation praktiziert.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Sprint-Planung in einem Scrum-Tool (Pseudocode)
public class SprintPlanning {
    public static void main(String[] args) {
        ProductBacklog backlog = new ProductBacklog();
        Sprint sprint = new Sprint("Sprint 5", 14); // 14 Tage Dauer
        
        // Priorisierte Backlog-Items auswählen
        List<BacklogItem> selectedItems = backlog.getTopItems(5);
        
        // Team schätzt Aufwand (z. B. in Story Points)
        for (BacklogItem item : selectedItems) {
            int effort = team.estimateEffort(item);
            sprint.addItem(item, effort);
        }
        
        // Sprint-Ziel definieren
        sprint.setGoal("Mitgliederverwaltung implementieren");
        
        System.out.println("Sprint geplant: " + sprint);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9b1
- **Vorgänger / Parent:** [[Scrum-Events]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Events]]
  - [[Scrum]]
