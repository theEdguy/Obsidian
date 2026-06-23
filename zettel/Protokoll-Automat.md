---
id: 108b8d96-c73b-4128-8be5-4d10e61e1e58
title: "Protokoll-Automaten"
date: 2026-06-23
tags:
  - software_engineering
  - automat
  - zustand
  - design
  - draft
source: "software_engineering_kapitel_12"
---

# [[Protokoll-Automaten]]

- **Kernkonzept:** Protokoll-Automaten sind Zustandsmaschinen, die explizit die erlaubten Aufrufe von Systemoperationen in bestimmten Zuständen modellieren. Sie definieren, unter welchen Bedingungen (Vor- und Nachbedingungen) Operationen ausgeführt werden dürfen, um die Systemkonsistenz zu gewährleisten.
- **Nutzen & Zweck:** Protokoll-Automaten lösen das Problem der unklaren Systemzustände und unerlaubten Operationsaufrufe, indem sie den Lebenszyklus von Objekten oder Komponenten formalisieren. Sie erhöhen die Übersichtlichkeit und Wartbarkeit von Software, da Entwickler stets nachvollziehen können, in welchem Zustand sich das System befindet und welche Operationen zulässig sind. Dadurch werden Fehler durch ungültige Zustandsübergänge vermieden und die Robustheit des Systems verbessert.
- **Abgrenzung & Grenzen:** Protokoll-Automaten sollten nicht eingesetzt werden, wenn das System keine klar definierten Zustände oder komplexe Zustandsübergänge aufweist, da der Aufwand für die Modellierung dann unnötig hoch ist. Alternativen wie einfache Zustandsvariablen oder informelle Dokumentation reichen in solchen Fällen aus. Zudem eignen sie sich weniger für Systeme mit hoher Dynamik oder häufig wechselnden Anforderungen, da die Pflege der Zustandsmaschine aufwendig werden kann. Im Vergleich zu klassischen Zustandsdiagrammen liegt der Fokus von Protokoll-Automaten stärker auf der formalen Definition von Operationsaufrufen und weniger auf der Visualisierung von Abläufen.
- **Beispiel / Code:** ```java
public enum State implements ProtocolState {
    Started,
    ValidationFailed,
    Login(Started, ValidationFailed),
    ManageMembers(EditMember, NotAllowed);
    
    private List<State> subStates;
    
    private State(State... subS) {
        this.subStates = new ArrayList<>(Arrays.asList(subS));
    }
    
    public boolean isAllowedOperation(String operation) {
        switch (this) {
            case Login:
                return operation.equals("validateToken");
            case ManageMembers:
                return operation.equals("editMember") || operation.equals("deleteMember");
            default:
                return false;
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3
- **Vorgänger / Parent:** [[Zustandsverwaltung]]
- **Folgezettel / Unterzettel:**
  - [[Zustandsdiagramme]]
  - [[Guard-Conditions]]
  - [[Action-Expressions]]
- **Querverweise:**
  - [[State-Pattern]]
  - [[Zustandsverwaltung]]
