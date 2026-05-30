---
id: 92682823-69e1-4ca8-80ce-08535fd30eaa
title: "Use-Case-Driven_Development"
date: 2026-05-30
tags:
  - software_engineering
  - software_process
  - agile
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Use-Case-Driven_Development]]

- **Kernkonzept:** [[Use-Case-Driven_Development]] ist ein [[Entwicklungsansatz]], bei dem [[Use_Case|Use-Cases]] die zentrale [[Steuerung]] für [[Analyse]], [[Design]], [[Implementierung]] und [[Test]] vorgeben. Der [[Entwicklungsprozess]] orientiert sich an den [[Anforderung|Anforderungen]] der [[Endbenutzer]].
- **Nutzen & Zweck:** Es stellt sicher, dass das [[Softwaresystem]] die [[funktionale_Anforderung|funktionalen Anforderungen]] der [[Stakeholder]] erfüllt und vermeidet [[Überentwicklung|Überentwicklungen]] oder [[Fehlentwicklung|Fehlentwicklungen]]. Es fördert die [[Iterative_Entwicklung|iterative Entwicklung]] und [[Risikominimierung]].
- **Abgrenzung & Grenzen:** Im Gegensatz zu [[Feature-Driven_Development]] oder [[Test-Driven_Development]] liegt der Fokus auf [[Use_Case|Use-Cases]] als [[Dokumentationsartefakt]] und [[Kommunikationsmittel]]. Es sollte nicht mit [[Ad-hoc-Entwicklung|Ad-hoc-Entwicklungen]] verwechselt werden, bei denen [[Anforderung|Anforderungen]] nicht systematisch erfasst werden.
- **Beispiel / Code:** ```plaintext
1. Priorisiere [[Use_Case|Use-Cases]] nach [[Risiko]] und [[Architekturrelevanz]].
2. Implementiere zuerst [[Use_Case|Use-Cases]], die die [[Architektur]] prägen (z. B. [[Mitglieder_verwalten]]).
3. Leite [[Testfall|Testfälle]] aus den [[Use_Case|Use-Cases]] ab.
```
