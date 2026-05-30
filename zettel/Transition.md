---
id: ccc3ba87-841f-4d0b-a1c9-1678bb7d8df3
title: "Transition"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Transition]]

- **Kernkonzept:** Eine [[Transition]] beschreibt den Wechsel von einem [[Zustand]] zu einem anderen in einer [[Zustandsmaschine]]. Sie wird durch einen [[Trigger]], eine optionale [[Guard-Condition]] und eine [[Aktion]] definiert.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung von [[Ablauf|Abläufen]] und [[Verhalten]] in [[Systemen]], indem sie [[Zustand|Zustände]] miteinander verbindet und [[Aktion|Aktionen]] bei Zustandswechseln ausführt. Dadurch wird die [[Steuerbarkeit]] und [[Nachvollziehbarkeit]] des [[Systems]] verbessert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Aktion|Aktionen]], die keinen Zustandswechsel erfordern. In solchen Fällen sind [[Interne_Transitionen]] vorzuziehen. Zudem können zu viele [[Transition|Transitionen]] die [[Komplexität]] der [[Zustandsmaschine]] erhöhen.
- **Beispiel / Code:** ```java
// Syntax: trigger [guard-condition] / action-expression
rightMouseDown(location) [location in window] /
    object := pickObject(location);
    object.highlight();
```
