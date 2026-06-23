---
id: e6b4f898-ba67-464e-a834-84f2b135df34
title: "Scrum-Rollen"
date: 2026-06-23
tags:
  - software_engineering
  - rolle
  - agile
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Scrum-Rollen]]

- **Kernkonzept:** Scrum-Rollen definieren klare [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Aufgabenbereich|Aufgabenbereiche]] innerhalb eines [[agile|agilen]] Projektteams, um die [[Zusammenarbeit]] und den Entwicklungsprozess strukturiert und effizient zu gestalten. Die drei zentralen [[Rolle|Rollen]] sind [[Product_Owner]], [[Scrum_Master]] und [[Development_Team]].
- **Nutzen & Zweck:** Scrum-Rollen existieren, um die [[Komplexität]] in [[Softwareentwicklungsprojekt|Softwareentwicklungsprojekten]] zu reduzieren, indem sie [[Transparenz]] über [[Zuständigkeit|Zuständigkeiten]] schaffen, [[Selbstorganisation]] des Teams fördern und klare [[Kommunikation]] ermöglichen. Sie lösen das Problem unklarer [[Verantwortlichkeit|Verantwortlichkeiten]], vermeiden [[Konflikt|Konflikte]] durch überlappende [[Aufgabenbereich|Aufgabenbereiche]] und ermöglichen eine zielgerichtete [[Priorisierung]] von [[Anforderung|Anforderungen]] (z. B. durch den [[Product_Owner]]). Zudem unterstützen sie die kontinuierliche [[Prozessoptimierung]] (durch den [[Scrum_Master]]) und stellen sicher, dass das Team gemeinsam auf die Lieferung wertvoller [[Produktinkrement|Produktinkremente]] hinarbeitet. Durch die klare Aufteilung der [[Rolle|Rollen]] wird die Effizienz gesteigert und die [[Agilität]] des Teams gestärkt.
- **Abgrenzung & Grenzen:** Scrum-Rollen sollten nicht in starren, hierarchischen oder nicht-agilen [[Organisationsstruktur|Organisationsstrukturen]] eingesetzt werden, in denen [[Entscheidungsprozess|Entscheidungsprozesse]] zentralisiert sind oder keine iterative Entwicklung möglich ist. Im Gegensatz zu traditionellen [[Rolle|Rollenmodellen]] wie dem [[Projektmanager]] im [[Wasserfallmodell]] sind Scrum-Rollen nicht auf Kontrolle, sondern auf [[Servant_Leadership]] und [[Selbstorganisation]] ausgelegt. Sie eignen sich weniger für Projekte mit festen, unveränderlichen [[Anforderung|Anforderungen]] oder für Teams, die keine [[cross-funktionale_Zusammenarbeit|cross-funktionale Zusammenarbeit]] ermöglichen können. Alternativen wie [[Kanban]] verzichten gänzlich auf feste [[Rolle|Rollen]] und setzen stattdessen auf kontinuierliche [[Workflow|Workflows]]. Zudem haben Scrum-Rollen keine disziplinarische [[Weisungsbefugnis]], was in streng hierarchischen Umgebungen zu Akzeptanzproblemen führen kann.
- **Beispiel / Code:** ```java
// Beispielhafte Darstellung der Verantwortlichkeiten in einem Scrum-Team (Pseudocode)
// Integriert die Priorisierung, Aufwandsschätzung und Kollaborationsunterstützung

class ScrumTeam {
    ProductOwner productOwner;
    ScrumMaster scrumMaster;
    DevelopmentTeam developmentTeam;
    
    public void startSprint(SprintGoal goal) {
        // Product Owner priorisiert Backlog
        productOwner.priorisiereBacklog("User Story: Login-Funktion", 1);
        
        // Development Team plant Sprint und schätzt Aufwand
        developmentTeam.planSprint(goal);
        developmentTeam.schaetzeAufwand("User Story: Login-Funktion", 5);
        
        // Scrum Master entfernt Hindernisse und moderiert
        scrumMaster.unterstuetzeTeam();
        scrumMaster.ermöglicheKollaboration(productOwner, developmentTeam);
    }
}

class ProductOwner {
    void priorisiereBacklog(String item, int prioritaet) {
        System.out.println("Priorisiere: " + item + " mit Priorität " + prioritaet);
    }
}

class ScrumMaster {
    void unterstuetzeTeam() {
        System.out.println("Hindernisse identifizieren und beseitigen.");
    }
    
    void ermöglicheKollaboration(Object... teilnehmer) {
        System.out.println("Moderiere Meeting mit " + teilnehmer.length + " Teilnehmern");
    }
}

class DevelopmentTeam {
    void planSprint(SprintGoal goal) {
        System.out.println("Sprint-Backlog erstellen und Aufgaben verteilen.");
    }
    
    void schaetzeAufwand(String item, int storyPoints) {
        System.out.println("Schätze Aufwand für " + item + ": " + storyPoints + " Story Points");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9a
- **Vorgänger / Parent:** [[Scrum]]
- **Folgezettel / Unterzettel:**
  - [[Product_Owner]]
  - [[Scrum_Master]]
  - [[Entwicklungsteam]]
- **Querverweise:**
  - [[Scrum]]
