---
id: 447f3eca-0951-4341-a022-5a4783c1d177
title: "State-Interface"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - zustand
  - interface
  - draft
source: "software_engineering_kapitel_12"
---

# [[State-Interface]]

- **Kernkonzept:** Das State-Interface ist ein Entwurfsmuster, das Zustände eines Objekts oder Systems als eigenständige Schnittstellen oder Typen modelliert. Es ermöglicht die klare Trennung von Zustandsspezifischer Logik und fördert die Erweiterbarkeit durch Implementierung zustandsspezifischer Verhalten in separaten Klassen.
- **Nutzen & Zweck:** Das State-Interface löst das Problem der unübersichtlichen und schwer wartbaren Zustandshandhabung in komplexen Systemen. Es vermeidet lange Bedingungsstrukturen (z. B. if-else oder switch-case) zur Zustandsprüfung, indem es zustandsspezifisches Verhalten in separate Klassen auslagert. Dadurch wird der Code modularer, leichter testbar und einfacher erweiterbar, insbesondere wenn neue Zustände hinzugefügt werden müssen. Zudem unterstützt es die Einhaltung von Vor- und Nachbedingungen, da jeder Zustand explizit definiert ist und Übergänge klar geregelt sind.
- **Abgrenzung & Grenzen:** Das State-Interface sollte nicht eingesetzt werden, wenn das System nur wenige, einfache Zustände besitzt, da der Overhead durch zusätzliche Klassen und Schnittstellen den Nutzen übersteigt. Es unterscheidet sich von einfachen Zustandsvariablen (z. B. Enums) durch die Kapselung von Verhalten in separaten Klassen, was bei trivialen Zustandswechseln unnötig komplex sein kann. Alternativen wie Zustandsautomaten mit Guards oder einfache boolesche Flags sind in solchen Fällen oft ausreichend. Zudem ist das Muster weniger geeignet, wenn Zustände stark voneinander abhängen oder globale Systemzustände modelliert werden müssen, die nicht klar in einzelne Objekte zerlegbar sind.
- **Beispiel / Code:** ```java
public interface State {
    boolean isSubStateOf(State state);
    boolean isSuperStateOf(State state);
}

public enum S implements State {
    Started,
    ValidationFailed,
    Login(Started, ValidationFailed);
    
    private List<State> subStates;
    
    private S(State... subS) {
        this.subStates = new ArrayList<>(Arrays.asList(subS));
    }
    
    @Override
    public boolean isSuperStateOf(State s) {
        boolean result = s == null || this == s;
        for (State state : this.subStates) {
            result |= state.isSuperStateOf(s);
        }
        return result;
    }
    
    @Override
    public boolean isSubStateOf(State state) {
        return state != null && state.isSuperStateOf(this);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[State-Pattern]]
- **Folgezettel / Unterzettel:**
  - [[Zustandsübergänge]]
  - [[Zustandsverwaltung]]
- **Querverweise:**
  - [[State-Pattern]]
  - [[Protokoll-Automaten]]
