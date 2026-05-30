---
id: a820cd5d-43de-46fb-8200-530c3b8a67a0
title: "Interne_Transitionen"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - zustandsdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Interne_Transitionen]]

- **Kernkonzept:** [[Interne_Transitionen]] sind [[Aktion|Aktionen]] innerhalb eines [[Zustands]], die durch [[Event|Events]] ausgelöst werden, ohne den [[Zustand]] selbst zu verlassen. Sie umfassen vordefinierte [[Aktion|Aktionen]] wie `entry`, `do`, `exit` oder benutzerdefinierte [[Event|Events]].
- **Nutzen & Zweck:** Sie ermöglichen die Kapselung von [[Verhalten]] innerhalb eines [[Zustands]], ohne die [[Zustandsmaschine]] zu verlassen. Dadurch wird die [[Wartbarkeit]] und [[Kohäsion]] der [[Zustandsmaschine]] erhöht.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Aktion|Aktionen]], die den [[Zustand]] ändern oder externe [[Systemkomponente|Systemkomponenten]] betreffen. In solchen Fällen sollten explizite [[Transition|Transitionen]] verwendet werden. Zudem können zu viele [[Interne_Transitionen]] die [[Lesbarkeit]] beeinträchtigen.
- **Beispiel / Code:** ```java
public class Zustand {
    public void onEntry() {
        System.out.println("Betrete Zustand");
    }
    
    public void onDo() {
        System.out.println("Führe Aktion im Zustand aus");
    }
    
    public void onEvent(Event event) {
        if (event == Event.BENUTZERDEFINIERT) {
            System.out.println("Benutzerdefiniertes Event verarbeitet");
        }
    }
}
```
