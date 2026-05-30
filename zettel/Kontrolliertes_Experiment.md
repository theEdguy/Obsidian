---
id: b7c2693c-104d-4fd2-9a9f-8bb7cfb15302
title: "Kontrolliertes_Experiment"
date: 2026-05-30
tags:
  - software_engineering
  - forschung
  - methode
  - empirische_forschung
  - experiment_design
  - draft
source: "SWE Slides (Folien 16-30)"
---

# [[Kontrolliertes_Experiment]]

- **Kernkonzept:** Eine [[empirische_Methode]], bei der [[Unabhängige_Variable|unabhängige Variablen]] gezielt manipuliert werden, um deren [[Einfluss]] auf [[Abhängige_Variable|abhängige Variablen]] und damit [[Ursache-Wirkungs-Beziehung|Ursache-Wirkungs-Beziehungen]] unter definierten [[Bedingung|Bedingungen]] zu messen, während andere [[Faktor|Faktoren]] konstant gehalten werden.
- **Nutzen & Zweck:** Ermöglicht die [[Validierung]] von [[Hypothese|Hypothesen]] unter kontrollierten [[Bedingung|Bedingungen]], um [[Kausalität]] nachzuweisen. Wird eingesetzt, um [[Werkzeug|Werkzeuge]], [[Methode|Methoden]], [[Algorithmus|Algorithmen]], [[Entwurfsmuster|Entwurfsmuster]] oder [[Performance-Optimierung|Performance-Optimierungen]] im [[Software-Engineering]] zu evaluieren und zu vergleichen.
- **Abgrenzung & Grenzen:** Aufwendig in der [[Durchführung]] und oft schwer auf reale [[Projekt|Projekte]] übertragbar, da die künstliche [[Kontrollierte_Umgebung|kontrollierte Umgebung]] die Übertragbarkeit der [[Ergebnis|Ergebnisse]] einschränkt. Erfordert sorgfältige [[Planung]], um [[Verzerrung|Verzerrungen]] zu vermeiden. Nicht geeignet für explorative Studien in realen Umgebungen; Alternativen sind [[Fallstudie|Fallstudien]] oder [[Umfrage|Umfragen]].
- **Beispiel / Code:** ```java
// Beispiel: Vergleich zweier [[Algorithmus|Algorithmen]] unter kontrollierten Bedingungen
int[] daten = {5, 2, 9, 1, 5}; // Unabhängige Variable: [[Algorithmus]]
long zeitBubbleSort = messZeit(() -> bubbleSort(daten.clone()));
long zeitQuickSort = messZeit(() -> quickSort(daten.clone()));
// Abhängige Variable: Ausführungszeit

// Beispiel aus der Praxis: Vergleich der [[Fehlerrate]] zweier [[Testmethode|Testmethoden]] in einem [[Labor]]-Setting
```
