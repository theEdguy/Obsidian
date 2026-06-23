---
id: c89a4e42-4448-402d-8668-f615bdaad908
title: "Iterationsdurchführung"
date: 2026-06-23
tags:
  - software_engineering
  - durchführung
  - iterativ
  - prozessmodell
  - draft
source: "software_engineering_kapitel_09"
---

# [[Iterationsdurchführung]]

- **Kernkonzept:** Die [[Iterationsdurchführung]] bezeichnet im [[Software_Engineering]] einen zyklischen [[Prozessmodell|Prozessschritt]] innerhalb [[iterativer_Entwicklung|iterativer Entwicklungsmodelle]], bei dem priorisierte [[Anforderung|Anforderungen]] in kurzen, festgelegten Zeitabschnitten (Iterationen) umgesetzt, getestet und bewertet werden, um kontinuierlich funktionierende [[Software-Inkrement|Software-Inkremente]] zu liefern. Jede Iteration erzeugt ein funktionsfähiges Teilprodukt, das auf Basis von [[Feedback]] weiter verbessert wird.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem starrer, sequenzieller [[Entwicklungsprozess|Entwicklungsprozesse]] wie dem [[Wasserfallmodell]], indem es frühzeitiges [[Feedback]], flexible Anpassungen an sich ändernde [[Anforderung|Anforderungen]] und schrittweise Verbesserung ermöglicht. Durch die iterative Vorgehensweise können komplexe [[Softwareprojekt|Softwareprojekte]] beherrschbar gemacht werden, da kontinuierliche [[Validierung]] und [[Risikomanagement|Risikominimierung]] durch regelmäßige [[Testphase|Testphasen]] und [[Stakeholder]]-Einbindung erfolgen. Dies fördert die Zusammenarbeit zwischen [[Entwicklungsteam|Entwicklungsteams]] und [[Stakeholder|Stakeholdern]], stellt sicher, dass kritische [[Funktionalität|Funktionalitäten]] priorisiert und zuerst realisiert werden, und steigert so kontinuierlich den [[Geschäftswert]]. Zudem ermöglicht die Iterationsdurchführung eine schrittweise [[Architekturoptimierung]] und [[Refactoring|Refaktorisierung]] der [[Codebasis]], um [[Technische_Schuld|technische Schulden]] frühzeitig zu adressieren.
- **Abgrenzung & Grenzen:** Die [[Iterationsdurchführung]] sollte nicht genutzt werden, wenn [[Anforderung|Anforderungen]] von Anfang an vollständig stabil und unveränderlich sind oder das [[Projekt]] extrem klein und einfach strukturiert ist, da der Overhead der Iterationsplanung und -koordination dann ineffizient wäre. Im Vergleich zu [[sequenziellen_Modell|sequenziellen Modellen]] wie dem [[Wasserfallmodell]] erfordert sie höheren Koordinationsaufwand und ist weniger vorhersehbar in Bezug auf Zeit- und Budgetplanung. Alternativen wie [[Kanban]] eignen sich besser für kontinuierliche, nicht in Zyklen gegliederte Arbeit, während [[Spiralmodell|Spiralmodelle]] stärker [[Risikomanagement|risikogetrieben]] sind. Bei unklaren [[Projektziel|Projektzielen]] oder mangelnder Disziplin im [[Team]] kann die Iterationsdurchführung zu Ineffizienzen führen, da sie eine kontinuierliche [[Priorisierung]], regelmäßige [[Review]]s und enge Zusammenarbeit voraussetzt. Zudem ist sie weniger geeignet für [[Projekt|Projekte]] mit extrem kurzen Laufzeiten oder klar definierten, unveränderlichen Ergebnissen.
- **Beispiel / Code:** ```java
// Beispiel für iterative Entwicklung in Scrum (Pseudocode)
public class Iteration {
    public static void main(String[] args) {
        List<String> productBacklog = Arrays.asList("[[User_Story|User Story]]: Benutzerlogin", 
                                                  "[[User_Story|User Story]]: Datenbankanbindung", 
                                                  "[[User_Story|User Story]]: UI-Optimierung", 
                                                  "[[User_Story|User Story]]: Performance-Analyse");
        
        for (int sprint = 1; sprint <= 3; sprint++) {
            System.out.println("Starte Sprint " + sprint + ":");
            List<String> sprintBacklog = priorisiereBacklog(productBacklog, sprint);
            
            // Tägliche Iterationsschritte (Daily Scrum)
            while (!sprintBacklog.isEmpty()) {
                String aufgabe = sprintBacklog.remove(0);
                implementiere(aufgabe);
                teste(aufgabe);
                
                // Tägliche Synchronisation
                if (blockersExist()) {
                    resolveBlockers();
                }
            }
            
            // Iterationsabschluss: Review und Retrospektive
            System.out.println("Sprint-Review: [[Feedback]] einholen und [[Product_Backlog|Product Backlog]] anpassen");
            deliverIncrement();
            conductSprintReview();
            conductRetrospective();
            
            productBacklog = aktualisiereBacklog(productBacklog, holeFeedback());
        }
    }
    
    private static List<String> priorisiereBacklog(List<String> backlog, int sprint) {
        // Priorisierung basierend auf [[Geschäftswert]] und [[Risiko]]
        return backlog.stream()
                      .sorted((a, b) -> prioritaetVon(a) - prioritaetVon(b))
                      .limit(sprintCapacity())
                      .collect(Collectors.toList());
    }
    
    private static void implementiere(String aufgabe) {
        System.out.println("Implementiere: " + aufgabe);
        // Umsetzung mit [[Testgetriebene_Entwicklung|testgetriebener Entwicklung]] (TDD)
    }
    
    private static void teste(String aufgabe) {
        System.out.println("Teste: " + aufgabe);
        // Automatisierte [[Unit_Test|Unit-Tests]] und [[Integrationstest|Integrationstests]]
    }
    
    private static List<String> aktualisiereBacklog(List<String> backlog, String feedback) {
        // Anpassung des Backlogs basierend auf [[Feedback]] und neuen [[Anforderung|Anforderungen]]
        return backlog.stream()
                      .filter(item -> !item.contains("abgeschlossen"))
                      .collect(Collectors.toList());
    }
    
    private static String holeFeedback() {
        return "Neue [[Anforderung|Anforderungen]]: Mobile Unterstützung";
    }
    
    private static void deliverIncrement() {
        System.out.println("[[Software-Inkrement|Inkrement]] ausgeliefert: Potenziell auslieferbares Produkt");
    }
    
    private static void conductSprintReview() {
        System.out.println("Sprint-Review: [[Stakeholder]]-Feedback einholen");
    }
    
    private static void conductRetrospective() {
        System.out.println("Retrospektive: Prozessverbesserungen identifizieren");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5b
- **Vorgänger / Parent:** [[Iterative_Entwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Implementierung]]
  - [[Test]]
- **Querverweise:**
  - [[Agile_Entwicklung]]
  - [[Software-Entwicklung]]
