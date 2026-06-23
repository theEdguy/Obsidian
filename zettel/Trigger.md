---
id: 650b300f-96a9-4763-9a36-f901d49cd1e0
title: "Trigger"
date: 2026-06-23
tags:
  - software_engineering
  - ereignis
  - operation
  - design
  - draft
source: "software_engineering_kapitel_12"
---

# [[Trigger]]

- **Kernkonzept:** Ein Trigger ist ein auslösendes Ereignis in einem Zustandsdiagramm oder Protokoll-Automaten, das eine Zustandsänderung oder eine Systemoperation initiiert. Er repräsentiert typischerweise einen Methodenaufruf, ein Signal oder ein Zeitereignis, das eine Transition zwischen Zuständen auslöst.
- **Nutzen & Zweck:** Trigger ermöglichen die Modellierung dynamischer Systemverhalten, indem sie definieren, unter welchen Bedingungen Zustandsübergänge stattfinden. Sie lösen konkrete Probleme wie die Steuerung von Abläufen in komplexen Systemen, indem sie sicherstellen, dass Operationen nur in zulässigen Zuständen ausgeführt werden. Dadurch erhöhen sie die Übersichtlichkeit und Wartbarkeit von Software, insbesondere bei der Implementierung von Protokollen oder Benutzeroberflächen.
- **Abgrenzung & Grenzen:** Trigger sollten nicht genutzt werden, wenn das Systemverhalten rein sequenziell oder ohne Zustandsabhängigkeiten modelliert werden kann, da sie zusätzliche Komplexität einführen. Alternativen wie einfache Methodenaufrufe oder ereignislose Zustandsmaschinen sind in solchen Fällen effizienter. Zudem unterscheiden sich Trigger von Guards, die lediglich Bedingungen prüfen, aber keine Aktionen auslösen. Bei hochfrequenten Ereignissen können Trigger zu Performance-Problemen führen, wenn sie unkontrolliert ausgelöst werden.
- **Beispiel / Code:** ```java
// Beispiel für einen Trigger in einer UML-Transition (Pseudocode-Syntax)
right-mouse-down(location) [location in window] / object := pickObject(location); object.highlight

// Beispiel für einen Trigger in einer Java-Implementierung einer Zustandsmaschine
public void handleEvent(Trigger trigger) {
    if (currentState.canHandle(trigger)) {
        currentState = currentState.transition(trigger);
        notifyObservers();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3c
- **Vorgänger / Parent:** [[Systemoperationen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Systemoperationen]]
  - [[Protokoll-Automaten]]
