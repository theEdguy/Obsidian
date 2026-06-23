---
id: f5074f3c-b547-42c5-b41c-ab2cbec13eeb
title: "Agile_Entwicklung"
date: 2026-06-24
tags:
  - software_engineering
  - prozessmodelle
  - agil
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Agile_Entwicklung]]

- **Kernkonzept:** Die [[Agile_Entwicklung]] ist ein [[iteratives_Prozessmodell|iteratives]] und [[inkrementelles_Prozessmodell|inkrementelles]] [[Prozessmodell]] in der [[Softwareentwicklung]], das auf [[Flexibilität]], kontinuierliche [[Verbesserung]], enge [[Zusammenarbeit]] mit [[Stakeholder|Stakeholdern]] und [[Kundenfeedback]] setzt, um schnell auf [[Änderung|Änderungen]] zu reagieren und funktionierende [[Software]] in kurzen [[Iteration|Iterationen]] (z. B. [[Sprint|Sprints]]) zu liefern.
- **Nutzen & Zweck:** Die [[Agile_Entwicklung]] löst das Problem starrer, langfristiger [[Planungsprozess|Planungsprozesse]] in traditionellen [[Prozessmodell|Modellen]] wie dem [[Wasserfallmodell]], die oft zu unflexiblen und nicht mehr bedarfsgerechten [[Ergebnis|Ergebnissen]] führen. Sie ermöglicht es [[Entwicklungsteam|Teams]], sich an wechselnde [[Anforderung|Anforderungen]], [[Marktbedingung|Marktbedingungen]] oder technische [[Herausforderung|Herausforderungen]] anzupassen, indem sie regelmäßige [[Reflexion]], [[Anpassung]] und frühe Auslieferung von [[Produktinkrement|Produktinkrementen]] fördert. Durch kurze [[Iteration|Iterationen]] und kontinuierliche [[Feedbackschleife|Feedbackschleifen]] werden [[Qualität]], [[Kundenzufriedenheit]] und [[Produktivität]] gesteigert. Zudem unterstützt sie die [[Effizienz]] der [[Entwicklung]] durch [[Selbstorganisation]], [[Priorisierung]] von Aufgaben nach [[Kundenwert]] und dient als Grundlage für [[Vorgehensmodell|agile Methoden]] wie [[Scrum]], [[Kanban]] und [[Extreme_Programming]].
- **Abgrenzung & Grenzen:** Die [[Agile_Entwicklung]] eignet sich weniger für [[Projekt|Projekte]] mit stabilen, klar definierten [[Anforderung|Anforderungen]] oder solchen, die strikte [[Dokumentation]], langfristige [[Planung]] oder regulatorische [[Vorgabe|Vorgaben]] erfordern, wie z. B. in [[sicherheitskritisches_System|sicherheitskritischen Systemen]] oder bei vertraglich festgelegten [[Spezifikation|Spezifikationen]]. Im Vergleich zu klassischen [[Vorgehensmodell|Vorgehensmodellen]] wie dem [[Wasserfallmodell]] fehlt oft eine umfassende [[Dokumentation]], was die [[Nachvollziehbarkeit]] und [[Wartbarkeit]] erschweren kann. Zudem erfordert sie eine hohe [[Disziplin]], [[Selbstorganisation]] und kontinuierliche [[Kommunikation]] im [[Team]], was bei unerfahrenen oder räumlich verteilten [[Team|Teams]] zu [[Herausforderung|Herausforderungen]] führen kann. Ohne konsequente [[Priorisierung]] kann dies zu unklaren [[Ziel|Zielen]] oder [[Scope_Creep|Scope Creep]] führen. Agilität ist kein Ersatz für [[Planung]], sondern ein Rahmenwerk, das [[Kollaboration]] und [[Iteration|Iterationen]] betont. Sie ist weniger geeignet für [[Team|Teams]], die keine selbstorganisierte Arbeitsweise oder regelmäßige [[Kommunikation]] praktizieren können.
- **Beispiel / Code:** ```plaintext
Scrum-Ablauf (erweitert):
1. [[Produkt-Backlog]] erstellen und nach [[Kundenwert]] priorisieren
2. [[Sprint-Planung]] (Sprint-Ziel definieren, [[Sprint-Backlog]] erstellen)
3. [[Sprint]] (1-4 Wochen) mit täglichem [[Daily_Scrum|Stand-up-Meeting]]
4. [[Sprint-Review]] (Präsentation des [[Produktinkrement|Produktinkrements]])
5. [[Retrospektive]] (Reflexion und Verbesserung des Prozesses)
6. [[Produktinkrement]] ausliefern und [[Backlog]] anpassen
```

```java
// Beispiel für ein agiles Artefakt: Ein erweitertes Scrum-Board als Java-Klasse
import java.util.ArrayList;
import java.util.List;

public class ScrumBoard {
    private List<String> todo;
    private List<String> inProgress;
    private List<String> done;
    private List<String> sprintBacklog;
    private String sprintGoal;

    public ScrumBoard() {
        this.todo = new ArrayList<>();
        this.inProgress = new ArrayList<>();
        this.done = new ArrayList<>();
        this.sprintBacklog = new ArrayList<>();
        this.sprintGoal = "";
    }

    public void setSprintGoal(String goal) {
        this.sprintGoal = goal;
    }

    public void addToSprintBacklog(String task) {
        sprintBacklog.add(task);
    }

    public void addTask(String task) {
        todo.add(task);
    }

    public void moveToInProgress(String task) {
        if (todo.remove(task)) {
            inProgress.add(task);
        }
    }

    public void moveToDone(String task) {
        if (inProgress.remove(task)) {
            done.add(task);
        }
    }

    public void reviewSprint() {
        System.out.println("Sprint Goal: " + sprintGoal);
        System.out.println("Completed Tasks: " + done);
    }
}
```
