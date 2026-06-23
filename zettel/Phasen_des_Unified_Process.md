---
id: d4682897-edf7-4115-b3f7-cfca2ec15323
title: "Phasen des Unified Process"
date: 2026-06-23
tags:
  - software_engineering
  - prozess
  - entwicklung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Phasen des Unified Process]]

- **Kernkonzept:** Der Unified Process (UP) ist ein iterativ-inkrementelles Vorgehensmodell für die Softwareentwicklung, das in vier Phasen unterteilt ist: Inception, Elaboration, Construction und Transition. Jede Phase besteht aus mehreren Iterationen und zielt auf die schrittweise Erstellung eines auslieferbaren Softwareprodukts ab.
- **Nutzen & Zweck:** Der Unified Process bietet einen strukturierten Rahmen, um komplexe Softwareprojekte systematisch zu planen, zu entwickeln und auszuliefern. Er löst das Problem unklarer Anforderungen, unvorhersehbarer Risiken und mangelnder Flexibilität in linearen Modellen, indem er iterative Entwicklung, kontinuierliches Feedback und schrittweise Verfeinerung ermöglicht. Dadurch wird die Anpassungsfähigkeit an sich ändernde Anforderungen erhöht und das Projektrisiko reduziert.
- **Abgrenzung & Grenzen:** Der Unified Process sollte nicht in Projekten mit sehr stabilen, klar definierten Anforderungen und geringem Risiko eingesetzt werden, da der iterative Ansatz zusätzlichen Overhead verursachen kann. Im Vergleich zu agilen Methoden wie Scrum ist der UP weniger flexibel und stärker dokumentengetrieben, was in dynamischen Umgebungen nachteilig sein kann. Für kleine Projekte oder Prototypen eignen sich schlankere Vorgehensmodelle besser.
- **Beispiel / Code:** ```java
// Beispiel: Iterative Entwicklung im Unified Process (vereinfacht)
public class SoftwareProject {
    private String phase; // Aktuelle Phase: "Inception", "Elaboration", "Construction", "Transition"
    private List<String> iterations;
    
    public void executeIteration() {
        switch (phase) {
            case "Inception":
                defineVisionAndScope(); // Anforderungen grob skizzieren
                break;
            case "Elaboration":
                refineArchitecture(); // Architektur und Risiken klären
                break;
            case "Construction":
                developIncrement(); // Funktionalität implementieren
                break;
            case "Transition":
                deployAndTest(); // Auslieferung und Feedback
                break;
        }
        iterations.add(phase + " Iteration abgeschlossen");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2
- **Vorgänger / Parent:** [[Unified_Process]]
- **Folgezettel / Unterzettel:**
  - [[Inception]]
  - [[Elaboration]]
  - [[Construction]]
  - [[Transition]]
- **Querverweise:**
  - [[Unified_Process]]
