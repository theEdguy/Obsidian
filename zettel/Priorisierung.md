---
id: bc9a9182-c5ed-41a0-bf1f-b7d53bb57496
title: "Priorisierung"
date: 2026-06-23
tags:
  - software_engineering
  - projektmanagement
  - anforderungsanalyse
  - planung
  - priorisierung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Priorisierung]]

- **Kernkonzept:** Die [[Priorisierung]] ordnet [[Anforderung|Anforderungen]], [[Anwendungsfall|Anwendungsfälle]] oder Aufgaben im [[Software_Engineering]] systematisch nach ihrer Wichtigkeit und Dringlichkeit, um die [[Entwicklungsplanung]] zu steuern und die zentralen [[Funktionalität|Funktionalitäten]] eines Systems fokussiert umzusetzen. Sie reduziert [[Entwicklungsrisiko|Entwicklungsrisiken]] und schafft Klarheit über die Reihenfolge der Implementierung.
- **Nutzen & Zweck:** Die [[Priorisierung]] löst das Problem der [[Ressourcenknappheit]] und unklarer [[Projektziel|Projektziele]], indem sie sicherstellt, dass kritische [[Systemkomponente|Systemkomponenten]] oder risikobehaftete [[Anforderung|Anforderungen]] zuerst umgesetzt werden. Sie unterstützt die [[Architekturplanung]], verhindert die frühzeitige Bindung von Ressourcen an unwichtige [[Feature|Features]] und optimiert die [[Projektsteuerung]]. Zudem hilft sie, [[Projektziel|Projektziele]] mit [[Kundenbedürfnis|Kundenbedürfnissen]] abzustimmen und schafft Transparenz in [[iterativen Entwicklungsprozess|iterativen Entwicklungsprozessen]] wie [[Scrum]] oder [[Kanban]]. Durch die Fokussierung auf essentielle [[Funktionalität|Funktionalitäten]] wird die Effizienz der Entwicklung gesteigert und die Wahrscheinlichkeit von [[Projektverzögerung|Projektverzögerungen]] oder Fehlentwicklungen verringert.
- **Abgrenzung & Grenzen:** Die [[Priorisierung]] ist kein Ersatz für eine [[Risikoanalyse]] oder [[Architekturentscheidung|Architekturentscheidungen]], da sie sich auf die inhaltliche Gewichtung von Aufgaben konzentriert, nicht auf technische Details oder Risikobewertungen. Sie sollte nicht angewendet werden, wenn alle [[Anforderung|Anforderungen]] gleich kritisch sind oder keine klare Bewertungsgrundlage existiert, da dies zu willkürlichen Entscheidungen führen kann. Im Gegensatz zur reinen [[Zeitplanung]] (z. B. [[Gantt-Diagramm|Gantt-Diagramme]]) fokussiert die [[Priorisierung]] nicht auf die zeitliche Abfolge, sondern auf die strategische Gewichtung von [[Aufgabe|Aufgaben]]. Alternativen wie 'First-Come-First-Served' oder Ad-hoc-Entscheidungen ignorieren strategische [[Projektziel|Projektziele]] und bergen höhere Risiken für [[Projektverzögerung|Projektverzögerungen]] oder Fehlentwicklungen.
- **Beispiel / Code:** ```text
Priorisierte Anwendungsfälle:
1. (Hoch) [[Bestellung_aufgeben|Bestellung aufgeben]]
2. (Mittel) [[Zahlung_durchführen|Zahlung durchführen]]
3. (Niedrig) [[Produktbewertung_abgeben|Produktbewertung abgeben]]
```

```java
// Beispiel für eine priorisierte Use-Case-Liste in Java (vereinfacht)
import java.util.*;

class UseCase {
    String name;
    int priority; // 1 = hoch, 2 = mittel, 3 = niedrig
    List<String> requirements;
    
    public UseCase(String name, int priority, List<String> requirements) {
        this.name = name;
        this.priority = priority;
        this.requirements = requirements;
    }
}

public class Priorisierung {
    public static void main(String[] args) {
        List<UseCase> useCases = new ArrayList<>();
        useCases.add(new UseCase("[[Mitglieder_verwalten|Mitglieder verwalten]]", 1, Arrays.asList("F1.1", "F1.2")));
        useCases.add(new UseCase("[[Rechnung_generieren|Rechnungen generieren]]", 2, Arrays.asList("F3.1")));
        useCases.add(new UseCase("[[Statistik_anzeigen|Statistiken anzeigen]]", 3, Arrays.asList("F4.2")));
        
        // Sortierung nach Priorität (aufsteigend)
        useCases.sort(Comparator.comparingInt(uc -> uc.priority));
        
        useCases.forEach(uc -> System.out.println("Prio " + uc.priority + ": " + uc.name));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2b1
- **Vorgänger / Parent:** [[Anforderungsklassifikation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Anforderungsklassifikation]]
  - [[Use_Case_Priorisierung]]
