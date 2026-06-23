---
id: e44b7c79-a90f-4f89-af67-31598f88d231
title: "State-Diagramme"
date: 2026-06-23
tags:
  - software_engineering
  - diagramm
  - zustand
  - uml
  - draft
source: "software_engineering_kapitel_12"
---

# [[State-Diagramme]]

- **Kernkonzept:** State-Diagramme (Zustandsdiagramme) sind eine UML-Diagrammart, die die möglichen Zustände eines Objekts, einer Komponente oder eines Systems sowie die Übergänge zwischen diesen Zuständen durch innere oder äußere Ereignisse visualisiert. Sie beschreiben, wie sich Attribute und Verhalten in Abhängigkeit vom aktuellen Zustand ändern.
- **Nutzen & Zweck:** State-Diagramme lösen das Problem der Komplexität in der Modellierung dynamischer Systeme, indem sie explizit darstellen, unter welchen Bedingungen Zustandswechsel stattfinden und welche Aktionen dabei ausgeführt werden. Sie ermöglichen es, Vor- und Nachbedingungen von Operationen klar zu definieren, die Systemlogik überschaubar zu halten und Fehler durch unerlaubte Zustandsübergänge zu vermeiden. Besonders nützlich sind sie für Systeme mit vielen möglichen Zuständen, wie z. B. Benutzeroberflächen, Protokolle oder Steuerungssysteme.
- **Abgrenzung & Grenzen:** State-Diagramme sollten nicht genutzt werden, wenn das System keine oder nur wenige Zustände aufweist, da der Modellierungsaufwand dann unnötig hoch ist. Alternativen wie Aktivitätsdiagramme eignen sich besser für die Darstellung von Workflows oder Algorithmen, während Sequenzdiagramme Interaktionen zwischen Objekten detaillierter abbilden. Bei rein statischen Systemen oder einfachen Abläufen sind State-Diagramme oft überdimensioniert. Zudem können sie bei sehr komplexen Systemen unübersichtlich werden, wenn zu viele Unterzustände oder parallele Zustände modelliert werden.
- **Beispiel / Code:** ```java
public enum State {
    STARTED,
    VALIDATION_FAILED,
    LOGIN(STARTED, VALIDATION_FAILED),
    EDIT_MEMBER,
    MANAGE_MEMBERS(EDIT_MEMBER);
    
    private final List<State> subStates;
    
    State(State... subStates) {
        this.subStates = Arrays.asList(subStates);
    }
    
    public boolean isSubStateOf(State state) {
        return state != null && (this == state || subStates.stream().anyMatch(s -> s.isSubStateOf(state)));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3a1
- **Vorgänger / Parent:** [[Zustandsdiagramme]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Protokoll-Automaten]]
  - [[UML]]
