---
id: 0cff0ace-e2b8-420b-b7fa-2e842a1521bd
title: "Iterationsplanung"
date: 2026-06-23
tags:
  - software_engineering
  - planung
  - iterativ
  - prozessmodell
  - draft
source: "software_engineering_kapitel_09"
---

# [[Iterationsplanung]]

- **Kernkonzept:** Die [[Iterationsplanung]] ist ein zentrales [[Konzept]] im [[iterativen_Softwareentwicklungsprozess]], bei dem die [[Arbeit]] in festgelegte [[Zeitabschnitte]] (Iterationen) unterteilt wird, um schrittweise und priorisiert funktionale [[Inkremente]] des [[Systems]] zu entwickeln. Sie verbindet [[Use-Case-Analyse]] mit zeitlicher und ressourcenbezogener Planung und definiert, welche [[Anforderung|Anforderungen]] in welcher Reihenfolge umgesetzt werden, basierend auf deren Kritikalität und [[Abhängigkeit|Abhängigkeiten]].
- **Nutzen & Zweck:** Die [[Iterationsplanung]] löst das Problem unklarer Priorisierung und unstrukturierter Entwicklung, indem sie sicherstellt, dass kritische [[Anforderung|Anforderungen]] und architekturrelevante [[Use-Case|Use Cases]] frühzeitig umgesetzt werden. Sie ermöglicht eine flexible Anpassung an Änderungen, reduziert [[Risiko|Risiken]] durch kontinuierliches [[Feedback]] und schafft Transparenz über [[Fortschritt]] und Aufwand. Dadurch wird die Entwicklung effizienter und zielgerichteter gesteuert. Zudem macht sie komplexe [[Softwareprojekt|Softwareprojekte]] beherrschbar, indem sie die [[Entwicklung]] in überschaubare, zeitlich begrenzte [[Phase|Phasen]] unterteilt. Dies fördert die Anpassungsfähigkeit an sich ändernde [[Anforderung|Anforderungen]], da in späteren Iterationen neue Erkenntnisse oder Prioritäten berücksichtigt werden können.
- **Abgrenzung & Grenzen:** Die [[Iterationsplanung]] sollte nicht genutzt werden, wenn [[Anforderung|Anforderungen]] vollständig stabil und vorhersehbar sind oder ein strikt sequenzielles [[Vorgehensmodell]] (z. B. [[Wasserfallmodell]]) vorgeschrieben ist. Sie eignet sich weniger für [[Projekt|Projekte]] mit geringem Komplexitätsgrad oder solchen, bei denen eine vollständige [[Spezifikation]] vorab möglich ist. Alternativen wie [[Kanban]] verzichten auf feste Iterationen und setzen stattdessen auf kontinuierlichen Fluss, was bei hochdynamischen Umgebungen vorteilhaft sein kann. Im Gegensatz zu starren [[Vorgehensmodell|Vorgehensmodellen]] erfordert sie diszipliniertes [[Requirements-Management]], da unklare Priorisierungen zu ineffizienten Iterationen führen können. Bei sehr kleinen [[Projekt|Projekten]] mit minimalem [[Risiko]] kann der Overhead der [[Iterationsplanung]] unnötig sein.
- **Beispiel / Code:** ```java
// Beispiel für eine vereinfachte Iterationsplanung in einem agilen Kontext (Scrum/Kanban)
public class IterationPlan {
    private String iterationName; // z. B. "Sprint 3"
    private LocalDate startDate;
    private LocalDate endDate;
    private List<UseCase> prioritizedUseCases;
    private List<Iteration> iterations;

    public void planIteration(List<UseCase> backlog) {
        // Priorisiere Use Cases nach Risiko, Architektur-Relevanz und Kritikalität
        this.prioritizedUseCases = backlog.stream()
            .sorted(Comparator.comparing(UseCase::getPriority).reversed()
                .thenComparing(UseCase::getArchitecturalImpact))
            .limit(5) // Kapazität der Iteration
            .collect(Collectors.toList());
    }
    
    public void planIterations(List<UseCase> backlog) {
        // Priorisiere Use Cases nach Kritikalität und Abhängigkeiten
        backlog.sort((uc1, uc2) -> uc1.getPriority().compareTo(uc2.getPriority()));
        
        // Weise Use Cases den Iterationen zu (z. B. 2-Wochen-Zyklen)
        for (int i = 0; i < backlog.size(); i++) {
            int iterationIndex = i / 5; // Annahme: 5 Use Cases pro Iteration
            if (iterationIndex >= iterations.size()) {
                iterations.add(new Iteration());
            }
            iterations.get(iterationIndex).addUseCase(backlog.get(i));
        }
    }
    
    public void adjustPlan(Feedback feedback) {
        // Passe die Planung basierend auf Feedback an
        if (feedback.isCritical()) {
            prioritizedUseCases.add(0, feedback.getNewUseCase());
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5a
- **Vorgänger / Parent:** [[Iterative_Entwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Priorisierung]]
  - [[Aufwandsschätzung]]
- **Querverweise:**
  - [[Agile_Entwicklung]]
  - [[Scrum]]
