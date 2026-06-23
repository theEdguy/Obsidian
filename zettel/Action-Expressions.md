---
id: 32e574d8-e7e9-42a4-aba7-2357d4703c71
title: "Action-Expressions"
date: 2026-06-23
tags:
  - software_engineering
  - aktion
  - pseudocode
  - automat
  - draft
source: "software_engineering_kapitel_12"
---

# [[Action-Expressions]]

- **Kernkonzept:** Action-Expressions sind Ausdrücke in Zustandsdiagrammen oder Protokoll-Automaten, die Aktionen beschreiben, die bei einem Zustandsübergang (Transition) ausgeführt werden. Sie definieren das Verhalten, das als Reaktion auf ein auslösendes Ereignis (Trigger) unter bestimmten Bedingungen (Guard-Condition) abläuft.
- **Nutzen & Zweck:** Action-Expressions existieren, um das Verhalten eines Systems während eines Zustandswechsels präzise und nachvollziehbar zu modellieren. Sie lösen das Problem, dass komplexe Abläufe in Zustandsautomaten ohne klare Handlungsanweisungen schwer verständlich oder implementierbar wären. Durch die Verwendung von Pseudocode oder konkreten Anweisungen ermöglichen sie eine direkte Umsetzung der modellierten Logik in ausführbaren Code und verbessern die Kommunikation zwischen Design und Implementierung.
- **Abgrenzung & Grenzen:** Action-Expressions sollten nicht genutzt werden, wenn das Systemverhalten ausschließlich durch einfache Zustandswechsel ohne zusätzliche Logik beschrieben werden kann, da sie dann unnötige Komplexität einführen. Sie unterscheiden sich von reinen Guard-Conditions, die nur Bedingungen für Übergänge prüfen, aber keine Aktionen auslösen. Alternativen wie separate Methodenaufrufe oder externe Skripte sind sinnvoll, wenn die Aktionen sehr umfangreich oder wiederverwendbar sein sollen, da Action-Expressions direkt in die Transition eingebettet sind und schwerer wartbar sein können.
- **Beispiel / Code:** ```java
// Beispiel einer Transition mit Action-Expression in UML-Notation:
right-mouse-down(location) [location in window] / object:=pick-object(location); object.highlight

// Entsprechende Implementierung in einer Zustandsmaschine:
public void handleRightMouseDown(Point location) {
    if (location.isWithin(window)) {
        GraphicObject object = pickObject(location);
        object.highlight();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3c
- **Vorgänger / Parent:** [[Protokoll-Automaten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Protokoll-Automaten]]
  - [[Zustandsübergänge]]
