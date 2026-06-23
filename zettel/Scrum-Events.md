---
id: 5524e1a0-9387-4a41-8a10-8167c07ff691
title: "Scrum-Events"
date: 2026-06-23
tags:
  - software_engineering
  - events
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Scrum-Events]]

- **Kernkonzept:** Scrum-Events sind vordefinierte, zeitlich begrenzte Meetings im Scrum-Framework, die den iterativen Entwicklungsprozess strukturieren und Transparenz, Inspektion sowie Anpassung ermöglichen. Sie umfassen Sprint Planning, Daily Scrum, Sprint Review, Sprint Retrospective und das Backlog Refinement.
- **Nutzen & Zweck:** Scrum-Events lösen das Problem unklarer Kommunikation, fehlender Synchronisation und mangelnder kontinuierlicher Verbesserung in agilen Projekten. Sie schaffen feste Rituale, um den Fortschritt zu überwachen, Hindernisse früh zu erkennen, die Zusammenarbeit zu fördern und die Produktqualität durch regelmäßige Feedbackschleifen zu steigern. Dadurch wird die Effizienz des Teams erhöht und die Ausrichtung auf die Projektziele sichergestellt.
- **Abgrenzung & Grenzen:** Scrum-Events sollten nicht genutzt werden, wenn das Projekt keine iterative Entwicklung erfordert oder starre, vorab definierte Abläufe verlangt, wie z. B. in klassischen Wasserfallmodellen. Im Vergleich zu unstrukturierten Ad-hoc-Meetings bieten Scrum-Events zwar klare Regeln, können jedoch bei zu strikter Anwendung zu Overhead führen, wenn das Team klein ist oder die Komplexität des Projekts gering. Alternativen wie Kanban setzen auf kontinuierlichen Fluss ohne feste Events, was flexibler, aber weniger vorhersagbar sein kann.
- **Beispiel / Code:** ```java
// Beispiel für eine Sprint-Retrospective-Struktur (Pseudocode)
public class SprintRetrospective {
    public static void main(String[] args) {
        Team team = new Team("Scrum-Team A");
        Sprint sprint = new Sprint("Sprint 5");
        
        // Drei zentrale Fragen der Retrospective
        List<String> feedback = team.gatherFeedback(
            "Was lief gut?",
            "Was lief nicht gut?",
            "Was können wir verbessern?"
        );
        
        ActionItems actionItems = team.defineActionItems(feedback);
        sprint.addImprovements(actionItems);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9b
- **Vorgänger / Parent:** [[Scrum]]
- **Folgezettel / Unterzettel:**
  - [[Sprint_Planning]]
  - [[Daily_Scrum]]
  - [[Sprint_Review]]
  - [[Sprint_Retrospective]]
- **Querverweise:**
  - [[Scrum]]
