---
id: 70b9572d-59f7-4e47-b838-09e0c299946f
title: "Sprint"
date: 2026-06-23
tags:
  - software_engineering
  - agile_methoden
  - scrum
  - agile
  - prozess
  - draft
source: "software_engineering_kapitel_06"
---

# [[Sprint]]

- **Kernkonzept:** Ein [[Sprint]] ist ein zeitlich begrenzter [[Entwicklungszyklus]] (meist 2–4 Wochen, maximal 2 Monate) in [[Scrum]] und anderen [[agile_Methoden|agilen Methoden]], in dem ein festgelegter Umfang an [[Anforderung|Anforderungen]] umgesetzt wird, um ein [[Inkrement]] der [[Software]] zu liefern. Jeder [[Sprint]] folgt einem strukturierten Ablauf: [[Sprint_Planung|Planung]], Umsetzung, [[Sprint_Review|Review]] und [[Retrospektive]].
- **Nutzen & Zweck:** [[Sprint|Sprints]] lösen das Problem starrer, langfristiger [[Projektplanung|Projektplanungen]], indem sie [[Flexibilität]] und [[Transparenz]] in den [[Entwicklungsprozess]] bringen. Sie ermöglichen es [[Team|Teams]], schnell auf [[Änderung|Änderungen]] zu reagieren, [[Risiko|Risiken]] früh zu erkennen und kontinuierlich funktionierende [[Software]] zu liefern. Durch die feste [[Zeitvorgabe]] und klare [[Zielsetzung|Zielsetzungen]] wird die [[Produktivität]] gesteigert, die [[Planungssicherheit]] erhöht und regelmäßiges [[Feedback]] durch [[Stakeholder|Stakeholder]] sichergestellt. Dies fördert die iterative Entwicklung und reduziert die Komplexität in [[Projekt|Projekten]] mit unsicheren oder sich ändernden [[Anforderung|Anforderungen]].
- **Abgrenzung & Grenzen:** [[Sprint|Sprints]] sind nicht für alle [[Projektart|Projektarten]] geeignet. Bei sehr kleinen [[Projektumfang|Projektumfängen]] oder [[Wartungsprojekt|Wartungsprojekten]] kann der Overhead der [[Sprint_Planung|Sprint-Planung]] unnötig sein. Im Gegensatz zum [[Wasserfallmodell]], das eine sequentielle Abarbeitung vorsieht, eignen sich [[Sprint|Sprints]] besonders für komplexe [[Projekt|Projekte]] mit unsicheren oder dynamischen [[Anforderung|Anforderungen]]. Zu kurze [[Sprint|Sprints]] können zu Fragmentierung führen, während zu lange [[Sprint|Sprints]] die [[Flexibilität]] einschränken. Bei [[Projekt|Projekten]] mit extrem stabilen [[Anforderung|Anforderungen]] oder sehr kurzen Laufzeiten können traditionelle [[Entwicklungsmodell|Entwicklungsmodelle]] effizienter sein.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Sprint-Planung in einem agilen Tool (Pseudocode)
public class Sprint {
    private String sprintName;
    private LocalDate startDate;
    private LocalDate endDate;
    private List<[[User_Story|UserStory]]> backlogItems;
    
    public Sprint(String sprintName, LocalDate startDate, LocalDate endDate) {
        this.sprintName = sprintName;
        this.startDate = startDate;
        this.endDate = endDate;
        this.backlogItems = new ArrayList<>();
    }
    
    public void addUserStory([[User_Story|UserStory]] story) {
        backlogItems.add(story);
    }
    
    public boolean isWithinSprintDuration() {
        long daysBetween = ChronoUnit.DAYS.between(startDate, endDate);
        return daysBetween >= 14 && daysBetween <= 60; // 2 Wochen bis 2 Monate
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** [[Iterative_Entwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Dauer_von_Iterationen]]
  - [[Umfang_einer_Iteration]]
  - [[Mini-Projekt]]
- **Querverweise:** keine
