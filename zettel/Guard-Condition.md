---
id: 8ab40320-b008-44d4-b65c-e0a4c95e6856
title: "Guard-Condition"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Guard-Condition]]

- **Kernkonzept:** Eine [[Guard-Condition]] ist eine boolesche Bedingung, die erfüllt sein muss, damit eine [[Transition]] in einer [[Zustandsmaschine]] ausgeführt wird. Sie steuert, ob ein [[Event]] eine [[Transition]] auslösen darf.
- **Nutzen & Zweck:** Sie ermöglicht die bedingte Steuerung von [[Transition|Transitionen]] und verhindert unerwünschte Zustandswechsel. Dadurch wird die [[Konsistenz]] und [[Sicherheit]] des [[Systems]] erhöht.
- **Abgrenzung & Grenzen:** Nicht notwendig, wenn alle [[Transition|Transitionen]] bedingungslos ausgeführt werden sollen. Eine übermäßige Verwendung von [[Guard-Condition|Guard-Conditions]] kann die [[Lesbarkeit]] und [[Wartbarkeit]] der [[Zustandsmaschine]] beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel für eine Guard-Condition
transition(Event.PRUEFUNG_BEGINNEN) [versucheVerfuegbar > 0] /
    versucheVerfuegbar--;
```
