---
id: 086878ca-90aa-4ef7-9f70-086e5649306b
title: "Prioritätsstufen"
date: 2026-06-23
tags:
  - software_engineering
  - priorisierung
  - stufen
  - draft
source: "software_engineering_kapitel_07"
---

# [[Prioritätsstufen]]

- **Kernkonzept:** Prioritätsstufen sind ein Klassifizierungssystem für Use Cases, um deren Wichtigkeit und Dringlichkeit in der Softwareentwicklung zu bewerten. Sie werden typischerweise in drei Stufen (1 = hoch, 2 = mittel, 3 = niedrig) eingeteilt und steuern die Reihenfolge der Umsetzung.
- **Nutzen & Zweck:** Prioritätsstufen lösen das Problem der Ressourcenallokation in Projekten, indem sie eine klare Entscheidungsgrundlage für die Bearbeitungsreihenfolge von Anforderungen schaffen. Sie ermöglichen es Teams, sich auf kritische Systemfunktionen zu konzentrieren, die architekturrelevant sind oder hohe Risiken bergen, und verhindern so die Verschwendung von Entwicklungszeit an weniger wichtige Features.
- **Abgrenzung & Grenzen:** Prioritätsstufen sollten nicht verwendet werden, wenn alle Anforderungen gleich kritisch sind oder wenn die Projektumsetzung streng sequenziell nach anderen Kriterien (z. B. gesetzliche Vorgaben) erfolgen muss. Sie unterscheiden sich von reinen Aufwandsschätzungen, da sie nicht den Entwicklungsaufwand, sondern den strategischen Wert eines Use Cases bewerten. Zudem sind sie kein Ersatz für detaillierte Risikoanalysen oder Abhängigkeitsmanagement zwischen Anforderungen.
- **Beispiel / Code:** ```java
// Beispiel für Prioritätszuweisung in einem Use-Case-Objekt
public class UseCase {
    private String name;
    private int priority; // 1 = hoch, 2 = mittel, 3 = niedrig
    private String description;
    
    public UseCase(String name, int priority, String description) {
        this.name = name;
        this.priority = priority;
        this.description = description;
    }
    
    public int getPriority() {
        return priority;
    }
    
    // Methode zur Sortierung von Use Cases nach Priorität
    public static List<UseCase> sortByPriority(List<UseCase> useCases) {
        useCases.sort(Comparator.comparingInt(UseCase::getPriority));
        return useCases;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1
- **Vorgänger / Parent:** [[Use_Case_Priorisierung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Priorisierung]]
