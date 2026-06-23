---
id: 55caf0f9-3784-4d7c-91f5-6dc7ad195fe4
title: "Agile Methoden"
date: 2026-06-24
tags:
  - software_engineering
  - methoden
  - prozess
  - entwicklung
  - agil
  - prozessmodell
  - draft
source: "software_engineering_kapitel_15"
---

# [[Agile Methoden]]

- **Kernkonzept:** [[Agile_Methoden|Agile Methoden]] sind iterative und inkrementelle [[Vorgehensmodell|Vorgehensmodelle]] in der [[Softwareentwicklung]], die durch flexible [[Planung]], kontinuierliche [[Anpassung]] und enge [[Zusammenarbeit]] mit [[Stakeholder|Stakeholdern]] gekennzeichnet sind. Sie priorisieren die frühe und regelmäßige Lieferung funktionsfähiger [[Software]] über umfangreiche [[Dokumentation]] und passen sich dynamisch an sich ändernde [[Anforderung|Anforderungen]] an, um [[Kundenzufriedenheit]] und [[Anpassungsfähigkeit]] zu maximieren.
- **Nutzen & Zweck:** [[Agile_Methoden|Agile Methoden]] adressieren die Schwächen starrer, sequenzieller [[Vorgehensmodell|Vorgehensmodelle]] wie dem [[Wasserfallmodell]] oder [[V-Modell]], die durch lange [[Entwicklungszyklus|Entwicklungszyklen]], mangelnde Flexibilität bei sich ändernden [[Anforderung|Anforderungen]] und späte [[Feedback|Rückmeldungen]] von [[Stakeholder|Stakeholdern]] geprägt sind. Durch kurze [[Iteration|Iterationen]] (z. B. [[Sprint|Sprints]]), kontinuierliches [[Feedback]] und selbstorganisierte [[Team|Teams]] wird die [[Anpassungsfähigkeit]] an dynamische [[Anforderung|Anforderungen]] erhöht, die [[Qualität]] der [[Software]] verbessert und die [[Kundenzufriedenheit]] gesteigert. Sie ermöglichen frühzeitige [[Ergebnis|Ergebnisse]], reduzieren [[Risiko|Risiken]] durch regelmäßige Überprüfung (z. B. [[Sprint-Review|Sprint-Reviews]]) und fördern die [[Zusammenarbeit]] zwischen [[Entwickler|Entwicklern]] und [[Auftraggeber|Auftraggebern]], um schneller auf [[Marktveränderung|Marktveränderungen]] zu reagieren. Zudem wird die [[Transparenz]] im [[Projekt]] durch tägliche [[Stand-up-Meeting|Stand-up-Meetings]] und [[Sprint-Review|Sprint-Reviews]] erhöht, was die [[Entscheidungsfindung]] beschleunigt und die [[Teamdynamik]] stärkt. Agile Ansätze lösen das Problem der mangelnden Anpassungsfähigkeit traditioneller Modelle, indem sie kurze [[Entwicklungszyklus|Zyklen]] nutzen, um nutzbare [[Teilergebnis|Teilergebnisse]] frühzeitig zu liefern und kontinuierliches [[Feedback]] zu integrieren.
- **Abgrenzung & Grenzen:** [[Agile_Methoden|Agile Methoden]] eignen sich nicht für [[Projekt|Projekte]] mit von Anfang an klar definierten, unveränderlichen [[Anforderung|Anforderungen]] oder solchen, die strikte regulatorische Vorgaben mit umfangreicher [[Dokumentation]] erfordern, wie sie in sicherheitskritischen [[System|Systemen]] (z. B. Luftfahrt oder Medizintechnik) üblich sind. Im Vergleich zu klassischen [[Vorgehensmodell|Vorgehensmodellen]] wie dem [[Wasserfallmodell]] oder [[V-Modell]] fehlt ihnen oft eine detaillierte [[Vorabplanung]], was bei komplexen, langfristigen [[Projekt|Projekten]] mit festen [[Budget|Budgets]] und [[Zeitplan|Zeitplänen]] zu Unsicherheiten führen kann. Sie sind weniger vorhersehbar in Bezug auf [[Zeitrahmen]] und [[Kostenrahmen]] und erfordern eine hohe [[Disziplin]] sowie kontinuierliche [[Kommunikation]] im [[Team]]. Herausforderungen können bei verteilten, unerfahrenen oder hierarchisch geprägten [[Team|Teams]] auftreten, da agile Ansätze eine Kultur der [[Offenheit]] und des [[Vertrauen|Vertrauens]] voraussetzen, die in traditionell geführten [[Organisation|Organisationen]] schwer zu etablieren sein kann. Alternativen wie das [[V-Modell]] oder [[Hybrides_Vorgehensmodell|hybride Vorgehensmodelle]] eignen sich besser für [[Projekt|Projekte]] mit stabilen Rahmenbedingungen.
- **Beispiel / Code:** ```java
// Beispiel für eine User Story in einem agilen Backlog (Jira-ähnlich)
public class UserStory {
    private String id;          // z.B. "US-1"
    private String description; // z.B. "Als [[Nutzer]] möchte ich meine [[Adresse]] ändern können, um meine Daten aktuell zu halten"
    private int storyPoints;    // Aufwandsschätzung (z.B. 3)
    private String status;      // z.B. "To Do", "In Progress", "Done"
    private List<String> acceptanceCriteria; // Akzeptanzkriterien für die [[Qualitätssicherung]]

    public UserStory(String id, String description, int storyPoints) {
        this.id = id;
        this.description = description;
        this.storyPoints = storyPoints;
        this.status = "To Do";
        this.acceptanceCriteria = new ArrayList<>();
    }

    public void addAcceptanceCriterion(String criterion) {
        acceptanceCriteria.add(criterion);
    }

    public void updateStatus(String newStatus) {
        this.status = newStatus;  // Statusänderung nach [[Sprint-Review]]
    }
}

// Beispiel für eine einfache Scrum-Implementierung mit Sprint-Planung
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;

public class ScrumTeam {
    private List<UserStory> backlog;
    private List<UserStory> sprintBacklog;
    private List<String> teamMembers;
    private int sprintDurationDays = 14;

    public ScrumTeam() {
        this.backlog = new ArrayList<>();
        this.sprintBacklog = new ArrayList<>();
        this.teamMembers = new ArrayList<>();
    }

    public void addUserStory(UserStory story) {
        backlog.add(story);
    }

    public void planSprint() {
        // Priorisierte User Stories aus dem Product Backlog in den Sprint Backlog übernehmen
        sprintBacklog = backlog.stream()
                .filter(story -> story.isPrioritized())
                .limit(calculateCapacity())
                .collect(Collectors.toList());
    }

    private int calculateCapacity() {
        // Vereinfachte Kapazitätsberechnung basierend auf Teamgröße und Sprint-Dauer
        return teamMembers.size() * sprintDurationDays / 2;
    }

    public void dailyStandup() {
        teamMembers.forEach(member -> {
            System.out.println(member + ": " +
                "Gestern: " + getYesterdayWork(member) + ", " +
                "Heute: " + getTodayPlan(member) + ", " +
                "Hindernisse: " + getImpediments(member));
        });
    }

    // Hilfsmethoden für das Daily Stand-up (vereinfacht)
    private String getYesterdayWork(String member) { /* ... */ return ""; }
    private String getTodayPlan(String member) { /* ... */ return ""; }
    private String getImpediments(String member) { /* ... */ return ""; }
}

// Beispiel für ein einfaches Scrum-Board (Task-Verwaltung in einem Sprint)
class ScrumBoard {
    private List<Task> backlog;
    private List<Task> inProgress;
    private List<Task> done;

    public ScrumBoard() {
        this.backlog = new ArrayList<>();
        this.inProgress = new ArrayList<>();
        this.done = new ArrayList<>();
    }

    public void moveToInProgress(Task task) {
        backlog.remove(task);
        inProgress.add(task);
    }

    public void completeTask(Task task) {
        inProgress.remove(task);
        done.add(task);
    }
}

class Task {
    private String description;
    private int storyPoints;
    // ...
}
```
