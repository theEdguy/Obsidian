---
id: f8491386-01de-4684-9bcf-bffc92772ca3
title: "Synchronisation"
date: 2026-06-23
tags:
  - software_engineering
  - synchronisation
  - parallelität
  - architektur
  - draft
source: "software_engineering_kapitel_12"
---

# [[Synchronisation]]

- **Kernkonzept:** Synchronisation in der Softwarearchitektur bezeichnet die Koordination paralleler Abläufe oder Zustände, um sicherzustellen, dass abhängige Prozesse erst dann fortfahren, wenn vorher definierte Bedingungen erfüllt sind. Dies wird oft durch Mechanismen wie Zustandsautomaten oder explizite Synchronisationspunkte realisiert.
- **Nutzen & Zweck:** Synchronisation löst das Problem der Race Conditions und inkonsistenter Zustände in parallelen oder verteilten Systemen. Sie stellt sicher, dass kritische Abschnitte nur unter kontrollierten Bedingungen ausgeführt werden, um Datenintegrität und korrekte Abläufe zu gewährleisten. Besonders in zustandsbasierten Systemen verhindert sie, dass Operationen in unzulässigen Zuständen ausgeführt werden.
- **Abgrenzung & Grenzen:** Synchronisation sollte nicht eingesetzt werden, wenn keine echten Abhängigkeiten zwischen Prozessen bestehen, da sie unnötige Komplexität und Performance-Overhead verursacht. Alternativen wie asynchrone Kommunikation oder lock-freie Algorithmen sind vorzuziehen, wenn Unabhängigkeit der Abläufe gegeben ist. Zudem kann übermäßige Synchronisation zu Deadlocks oder Livelocks führen, wenn sie nicht sorgfältig entworfen wird. Im Gegensatz zu einfachen Mutex-Locks ermöglicht eine zustandsbasierte Synchronisation feingranularere Kontrolle, erfordert aber auch detailliertere Modellierung.
- **Beispiel / Code:** ```java
// Beispiel für Synchronisation in einem Zustandsautomaten mit UML-Transitionen
public class Studienverlauf {
    private State currentState = State.VORLESUNG;
    
    public synchronized void pruefungAblegen() {
        if (currentState != State.LABOR_ABGESCHLOSSEN) {
            throw new IllegalStateException("Prüfung kann erst nach Laborabschluss abgelegt werden!");
        }
        currentState = State.PRUEFUNG_BESTANDEN;
    }
    
    public enum State {
        VORLESUNG, LABOR, LABOR_ABGESCHLOSSEN, PRUEFUNG_BESTANDEN
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c2a
- **Vorgänger / Parent:** [[Nebenläufigkeit]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Nebenläufigkeit]]
  - [[State-Pattern]]
