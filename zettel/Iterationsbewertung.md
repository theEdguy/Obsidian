---
id: 28367eea-c1aa-4f42-9913-59d54c537bbb
title: "Iterationsbewertung"
date: 2026-06-23
tags:
  - software_engineering
  - bewertung
  - iterativ
  - prozessmodell
  - draft
source: "software_engineering_kapitel_09"
---

# [[Iterationsbewertung]]

- **Kernkonzept:** Die [[Iterationsbewertung]] ist ein systematischer Prozess zur Analyse und Bewertung der Ergebnisse einer [[Iterative_Entwicklung|Entwicklungsiteration]] im [[Software_Engineering]], um Fortschritt, [[Qualitätssicherung|Qualität]] und Risiken zu beurteilen sowie gezielte [[Anpassung|Anpassungen]] für nachfolgende [[Iteration|Iterationen]] abzuleiten. Sie dient als zentraler Bestandteil iterativer [[Prozessmodell|Prozessmodelle]] wie [[Scrum]] oder [[Unified_Process]], um kontinuierliche Verbesserungen zu ermöglichen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um in iterativen [[Entwicklungsprozess|Entwicklungsprozessen]] den Projektfortschritt zu messen, [[Schwachstelle|Schwachstellen]] frühzeitig zu erkennen und die [[Anforderungsanalyse|Anpassung von Anforderungen]] oder Prioritäten zu ermöglichen. Es löst das Problem statischer Planungen in komplexen [[Softwareprojekt|Softwareprojekten]], indem es regelmäßige [[Reflexion]] und flexible [[Anpassung]] an sich ändernde Rahmenbedingungen fördert. Dadurch werden Transparenz für [[Stakeholder]] erhöht, [[Risikomanagement|Risiken]] minimiert und die Effizienz des [[Entwicklungsteam|Teams]] gesteigert. Im Gegensatz zu einmaligen [[Meilenstein|Meilenstein-Reviews]] ermöglicht die [[Iterationsbewertung]] zyklische, inkrementelle Verbesserungen und unterstützt die [[Agile_Entwicklung|agile]] Philosophie der kontinuierlichen [[Feedbackschleife|Feedbackschleifen]].
- **Abgrenzung & Grenzen:** Die [[Iterationsbewertung]] sollte nicht in streng sequenziellen oder [[Wasserfallmodell|wasserfallartigen]] [[Projektmanagement|Projekten]] eingesetzt werden, da diese keine regelmäßigen [[Feedbackschleife|Feedbackschleifen]] vorsehen. Im Gegensatz zu [[Retrospektive|Retrospektiven]], die sich primär auf [[Teamdynamik]] und Prozesse konzentrieren, umfasst die [[Iterationsbewertung]] zusätzlich eine technische und funktionale Evaluation der Ergebnisse, einschließlich [[Metrik|Metriken]], [[Testbericht|Testberichten]] und [[Nutzerfeedback]]. Sie ist keine reine [[Statusbesprechung]], sondern erfordert eine strukturierte Analyse von [[Qualitätskriterium|Qualitätskriterien]] und [[Leistungsindikator|Leistungsindikatoren]]. Zudem ist sie weniger geeignet für [[Projekt]]e mit stabilen, unveränderlichen [[Anforderung|Anforderungen]], da ihr Fokus auf der kontinuierlichen [[Anpassung]] und [[Optimierung]] liegt.
- **Beispiel / Code:** ```java
// Beispiel: Struktur einer Iterationsbewertung in Scrum (Retrospektive) mit erweiterten Metriken
public class IterationReview {
    private int completedUserStories;
    private int openDefects;
    private double teamVelocity;
    private List<String> positives;
    private List<String> improvements;
    
    public IterationReview() {
        this.positives = Arrays.asList(
            "Implementierung der [[Mitgliederverwaltung]] abgeschlossen",
            "[[Teamkommunikation]] verbessert",
            "[[Testabdeckung]] um 15% erhöht"
        );
        this.improvements = Arrays.asList(
            "[[Testabdeckung]] auf kritische Module fokussieren",
            "[[Dokumentation]] aktualisieren und versionieren",
            "[[Code_Review|Code-Reviews]] für komplexe [[Algorithmus|Algorithmen]] einführen"
        );
    }
    
    public void evaluateIteration() {
        // Qualitätsbewertung basierend auf User Stories und Defekten
        double qualityScore = (completedUserStories * 10.0) / (completedUserStories + openDefects);
        
        System.out.println("Positives der Iteration:");
        positives.forEach(System.out::println);
        
        System.out.println("\nVerbesserungspotenzial:");
        improvements.forEach(System.out::println);
        
        System.out.println("\nMetriken:");
        System.out.printf("Qualitäts-Score: %.2f (Schwellenwert: 7.0)%n", qualityScore);
        System.out.printf("Team-Velocity: %.2f (Erwartet: %.2f)%n", teamVelocity, expectedVelocity());
        
        if (qualityScore < 7.0) {
            System.out.println("\nWarnung: Qualität der Iteration unter Schwellenwert! Maßnahmen einleiten.");
        }
        
        if (teamVelocity < expectedVelocity()) {
            System.out.println("Hinweis: Team-Velocity gesunken. Ursachenanalyse erforderlich.");
        }
    }
    
    private double expectedVelocity() {
        return 45.0; // Beispielwert basierend auf historischen Daten
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5c
- **Vorgänger / Parent:** [[Iterative_Entwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Retrospektive]]
  - [[Anpassung]]
- **Querverweise:**
  - [[Agile_Entwicklung]]
  - [[Qualitätssicherung]]
