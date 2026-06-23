---
id: 4b253903-77ff-4c37-ad62-a6da3d3a9aa8
title: "Increment"
date: 2026-06-23
tags:
  - software_engineering
  - increment
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Increment]]

- **Kernkonzept:** Ein Increment im Kontext von Scrum bezeichnet die Summe aller in einem Sprint fertiggestellten Product-Backlog-Einträge, die ein nutzbares, potenziell auslieferbares Produktinkrement darstellen. Es ist das Ergebnis der gemeinsamen Arbeit des Entwicklungsteams während eines Sprints und muss den Definition-of-Done-Kriterien entsprechen.
- **Nutzen & Zweck:** Das Konzept des Increments existiert, um kontinuierlich messbaren Fortschritt in der Produktentwicklung zu ermöglichen und sicherzustellen, dass nach jedem Sprint ein funktionsfähiges, qualitativ hochwertiges Produktteilstück vorliegt. Es löst das Problem, dass Entwicklungsprozesse ohne klare Zwischenziele oft zu unfertigen oder nicht integrierbaren Ergebnissen führen, und ermöglicht frühzeitiges Feedback sowie iterative Verbesserungen durch regelmäßige Lieferung nutzbarer Funktionalitäten.
- **Abgrenzung & Grenzen:** Ein Increment sollte nicht genutzt werden, wenn das Projekt oder Produkt keine iterative Entwicklung erfordert oder wenn die Anforderungen so stabil und vorhersehbar sind, dass ein sequenzieller Wasserfall-Ansatz sinnvoller ist. Es unterscheidet sich von klassischen Meilensteinen dadurch, dass es nicht nur einen Zwischenstand, sondern ein tatsächlich nutzbares Produktteil darstellt, das unabhängig von weiteren Sprints ausgeliefert werden könnte. Zudem ist es keine einzelne User Story oder Aufgabe, sondern die kumulative Summe aller abgeschlossenen Arbeiten eines Sprints.
- **Beispiel / Code:** ```java
// Beispiel: Definition-of-Done für ein Increment in einem Scrum-Projekt
public class DefinitionOfDone {
    public static boolean isIncrementComplete(ProductBacklogItem item) {
        return item.isCoded() &&
               item.isTested() &&
               item.isDocumented() &&
               item.isIntegrated() &&
               item.isReviewedByProductOwner();
    }
}

// Nach einem Sprint: Überprüfung, ob alle Items das Increment bilden
public class SprintReview {
    public static void main(String[] args) {
        List<ProductBacklogItem> sprintBacklog = getSprintBacklog();
        boolean isIncrementReady = sprintBacklog.stream()
            .allMatch(DefinitionOfDone::isIncrementComplete);
        
        if (isIncrementReady) {
            System.out.println("Increment ist fertig und potenziell auslieferbar!");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9c3
- **Vorgänger / Parent:** [[Scrum-Artefakte]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Artefakte]]
  - [[Scrum]]
