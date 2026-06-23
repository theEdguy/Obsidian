---
id: 928d78ba-dc7f-4b89-abe1-d65ba003358e
title: "Fassaden-Interface"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - interface
  - schnittstelle
  - draft
source: "software_engineering_kapitel_12"
---

# [[Fassaden-Interface]]

- **Kernkonzept:** Ein Fassaden-Interface ist eine Schnittstelle, die als vereinfachte und kontrollierte Zugangsschicht zu einem komplexen Subsystem oder einer Komponente dient. Es kapselt die interne Logik und bietet eine klare, reduzierte API für externe Nutzer.
- **Nutzen & Zweck:** Das Fassaden-Interface existiert, um die Komplexität von Subsystemen zu verbergen und die Kommunikation zwischen Komponenten zu minimieren. Es löst das Problem der unkontrollierten Abhängigkeiten, indem es Zugriffe kanalisiert, Zustände überwacht und die Konsistenz des Systems sicherstellt. Zudem ermöglicht es eine zentrale Steuerung von Systemoperationen und vereinfacht die Nutzung durch externe Module.
- **Abgrenzung & Grenzen:** Ein Fassaden-Interface sollte nicht genutzt werden, wenn das Subsystem sehr einfach ist oder keine Kapselung benötigt. Es unterscheidet sich von direkten Schnittstellen dadurch, dass es nicht nur Methoden bereitstellt, sondern auch zusätzliche Verantwortlichkeiten wie Zustandsprüfung, Nebenläufigkeitskontrolle oder Delegation übernimmt. Alternativen wie direkte Objektinteraktion oder Dependency Injection können sinnvoller sein, wenn keine zentrale Steuerung erforderlich ist.
- **Beispiel / Code:** ```java
public interface MemberManagement {
    void manageMembers(Token token);
}

class ManagementFacade implements MemberManagement {
    private StateMachine stateMachine;
    private ManageMembers manager = new ManageMembers();

    public synchronized void manageMembers(Token token) {
        if (!this.stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            return;
        }
        this.manager.manageMembers(token);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a
- **Vorgänger / Parent:** [[Fassaden-Pattern]]
- **Folgezettel / Unterzettel:**
  - [[Fassaden-Implementierung]]
- **Querverweise:**
  - [[Fassaden-Pattern]]
  - [[Schnittstellenverwaltung]]
