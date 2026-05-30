---
id: b0edfa68-634d-49d5-856a-7280427f0d20
title: "Iteratives_Projektmanagement"
date: 2026-05-30
tags:
  - software_engineering
  - projektmanagement
  - agile_methoden
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Iteratives_Projektmanagement]]

- **Kernkonzept:** Ein [[Vorgehensmodell|Vorgehensmodell]] in der [[Softwareentwicklung]], bei dem die Entwicklung in wiederholbaren [[Iteration|Iterationen]] mit festen Zeitvorgaben und definiertem Umfang erfolgt. Ziel ist die schrittweise Verbesserung des [[Produkt|Produkts]] durch regelmäßige Feedbackschleifen.
- **Nutzen & Zweck:** Löst das Problem der Unvorhersehbarkeit in [[Softwareprojekt|Softwareprojekten]] durch inkrementelle Fortschritte und kontinuierliche Anpassung an sich ändernde [[Anforderung|Anforderungen]]. Ermöglicht frühzeitige Risikoerkennung und transparente Fortschrittskontrolle.
- **Abgrenzung & Grenzen:** Nicht geeignet für Projekte mit extrem stabilen [[Anforderung|Anforderungen]] und klar definierten Zielen, bei denen ein [[Wasserfallmodell]] effizienter sein kann. Erfordert disziplinierte [[Synchronisation]] von [[Dokumentation]] und [[Modell|Modellen]] während der [[Iteration|Iterationen]].
- **Beispiel / Code:** ```java
// Beispiel für ein Task Board in einer Iteration
public class TaskBoard {
    private List<Task> toDo;
    private List<Task> inProgress;
    private List<Task> toVerify;
    private List<Task> done;

    public void moveTask(Task task, TaskStatus newStatus) {
        // Logik zur Aktualisierung des Arbeitsstands
    }
}
```
