---
id: 55cce520-8a9b-4fcb-95eb-309de7a576ff
title: "Synchronisierung_in_Zustandsmaschinen"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Synchronisierung_in_Zustandsmaschinen]]

- **Kernkonzept:** Die [[Synchronisierung_in_Zustandsmaschinen|Synchronisierung]] stellt sicher, dass bestimmte [[Transition|Transitionen]] in einer [[Zustandsmaschine]] erst dann ausgeführt werden, wenn vorher definierte [[Zustand|Zustände]] erreicht sind. Dies verhindert inkonsistente [[Systemzustand|Systemzustände]].
- **Nutzen & Zweck:** Sie löst das Problem der [[Abhängigkeit|Abhängigkeiten]] zwischen [[Ablauf|Abläufen]], z. B. wenn eine [[Prüfung]] erst nach Abschluss eines [[Labors]] abgelegt werden darf. Dadurch wird die [[Konsistenz]] des [[Systems]] sichergestellt.
- **Abgrenzung & Grenzen:** Nicht notwendig, wenn [[Ablauf|Abläufe]] vollständig unabhängig sind. Eine übermäßige [[Synchronisierung_in_Zustandsmaschinen|Synchronisierung]] kann zu [[Deadlock|Deadlocks]] oder unnötiger [[Komplexität]] führen. Alternativen wie [[Event-gesteuerte_Synchronisierung]] können flexibler sein.
- **Beispiel / Code:** ```java
// Beispiel für eine synchronisierte Transition
public void transition(Event event) {
    if (currentState == State.LABOR_TEIL_2 && event == Event.PRUEFUNG_BEGINNEN) {
        currentState = State.PRUEFUNG_ABLEGEN;
    }
}
```
