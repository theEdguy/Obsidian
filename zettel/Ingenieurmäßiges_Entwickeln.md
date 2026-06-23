---
id: 0b5541c6-26fd-42f7-827b-a65313863dfe
title: "Ingenieurmäßiges_Entwickeln"
date: 2026-06-24
tags:
  - software_engineering
  - methodik
  - empirie
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Ingenieurmäßiges_Entwickeln]]

- **Kernkonzept:** Anwendung [[wissenschaftlich_fundierter_Methoden]] und [[empirischer_Forschung]] in der [[Software-Entwicklung]], um reproduzierbare und nachvollziehbare Ergebnisse zu erzielen.
- **Nutzen & Zweck:** Reduziert [[Risiken]] und erhöht die [[Qualität]] durch systematische [[Analyse]], [[Design]] und [[Evaluation]]. Ermöglicht die Übertragbarkeit von Lösungen auf ähnliche Probleme.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Intuition]] oder [[Erfahrung]], sondern eine Ergänzung. Unterscheidet sich von [[Trial_and_Error]] durch strukturierte [[Hypothesenbildung]] und [[Validierung]]. Nicht sinnvoll bei explorativen Prototypen ohne klare Ziele.
- **Beispiel / Code:** ```java
// Beispiel für empirische Methode: Kontrolliertes Experiment
public void testPerformance(Algorithm algorithm) {
    long startTime = System.nanoTime();
    algorithm.execute();
    long duration = System.nanoTime() - startTime;
    System.out.println("Ausführungszeit: " + duration + " ns");
}
```
