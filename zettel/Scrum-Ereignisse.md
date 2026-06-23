---
id: d7aa0cec-12a5-4971-9a54-65fd3f373102
title: "Scrum-Ereignisse"
date: 2026-06-23
tags:
  - software_engineering
  - ereignis
  - agile
  - draft
source: "software_engineering_kapitel_05"
---

# [[Scrum-Ereignisse]]

- **Kernkonzept:** Scrum-Ereignisse sind fest definierte Meetings im agilen Rahmenwerk Scrum, die den regelmäßigen Austausch, die Planung, Überprüfung und Anpassung des Arbeitsfortschritts innerhalb eines Sprints strukturieren. Sie umfassen Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective und das Sprint Backlog Refinement.
- **Nutzen & Zweck:** Scrum-Ereignisse existieren, um Transparenz, Inspektion und Anpassung im Entwicklungsprozess zu gewährleisten. Sie lösen das Problem unklarer Prioritäten, mangelnder Kommunikation und fehlender kontinuierlicher Verbesserung, indem sie feste Zeitfenster für Reflexion und Koordination schaffen. Dadurch wird die Effizienz gesteigert und die Teamarbeit synchronisiert.
- **Abgrenzung & Grenzen:** Scrum-Ereignisse sollten nicht genutzt werden, wenn das Projekt keine iterative Entwicklung erfordert oder starre Vorgaben ohne Anpassungsbedarf hat. Im Gegensatz zu klassischen Projektmanagement-Methoden wie dem Wasserfallmodell, das sequenzielle Phasen vorsieht, sind Scrum-Ereignisse auf Flexibilität und kurze Feedbackschleifen ausgelegt. Sie eignen sich weniger für Projekte mit klar definierten, unveränderlichen Anforderungen oder für Teams, die keine Selbstorganisation praktizieren können.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Sprint-Planung (Pseudocode)
public class SprintPlanning {
    private Team team;
    private ProductBacklog backlog;
    private SprintGoal sprintGoal;

    public void planSprint() {
        List<BacklogItem> selectedItems = team.selectItems(backlog, sprintGoal);
        SprintBacklog sprintBacklog = new SprintBacklog(selectedItems);
        team.commitToSprint(sprintBacklog);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d3
- **Vorgänger / Parent:** [[Scrum]]
- **Folgezettel / Unterzettel:**
  - [[Sprint_Planning]]
  - [[Daily_Scrum]]
  - [[Sprint_Review]]
  - [[Sprint_Retrospective]]
- **Querverweise:**
  - [[Scrum]]
