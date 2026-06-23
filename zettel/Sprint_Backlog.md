---
id: 7d2a6b99-a315-4443-a0a5-44072b6b79d0
title: "Sprint Backlog"
date: 2026-06-23
tags:
  - software_engineering
  - sprint_backlog
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Sprint Backlog]]

- **Kernkonzept:** Das Sprint Backlog ist eine dynamische Liste von Aufgaben, die während eines Sprints in Scrum umgesetzt werden sollen. Es enthält detaillierte Arbeitspakete, die aus dem Product Backlog abgeleitet und für die Umsetzung im aktuellen Sprint priorisiert wurden.
- **Nutzen & Zweck:** Das Sprint Backlog dient der transparenten Planung und Steuerung der Arbeit im Sprint. Es löst das Problem der unklaren Arbeitsverteilung und ermöglicht dem Entwicklungsteam, sich auf konkrete, umsetzbare Aufgaben zu konzentrieren. Durch die tägliche Aktualisierung wird der Fortschritt sichtbar, und das Team kann flexibel auf Veränderungen reagieren, ohne das Sprint-Ziel zu gefährden.
- **Abgrenzung & Grenzen:** Das Sprint Backlog sollte nicht genutzt werden, wenn das Projekt keine iterative Entwicklung erfordert oder wenn Anforderungen starr und unveränderlich sind. Es unterscheidet sich vom Product Backlog dadurch, dass es nur die Aufgaben für einen einzelnen Sprint enthält und nicht die langfristige Roadmap. Im Gegensatz zu klassischen Projektplänen ist es kein statisches Dokument, sondern wird kontinuierlich angepasst. Für Projekte mit festen Lieferterminen und unveränderlichen Anforderungen eignen sich traditionelle Projektmanagement-Methoden besser.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Sprint-Backlog-Struktur in Java (als POJO)
public class SprintBacklog {
    private String sprintGoal;
    private List<Task> tasks;
    private LocalDate sprintStart;
    private LocalDate sprintEnd;

    public static class Task {
        private String id;
        private String description;
        private TaskStatus status;
        private int estimatedHours;
        private String assignee;

        // Getter und Setter
    }

    public enum TaskStatus {
        TODO, IN_PROGRESS, DONE
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9c2
- **Vorgänger / Parent:** [[Scrum-Artefakte]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Artefakte]]
  - [[Scrum]]
