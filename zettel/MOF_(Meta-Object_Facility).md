---
id: d71e688c-d415-4960-879b-d55e27363757
title: "MOF_(Meta-Object_Facility)"
date: 2026-05-30
tags:
  - software_engineering
  - metamodellierung
  - standard
  - uml
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[MOF_(Meta-Object_Facility)]]

- **Kernkonzept:** Ein [[Standard]] der [[OMG]] zur Definition von [[Meta-Modell|Meta-Modellen]] und [[Modellierungssprache|Modellierungssprachen]]. Bildet die Grundlage für [[UML]] und andere [[Modellierungssprache|Modellierungssprachen]].
- **Nutzen & Zweck:** Ermöglicht die formale Definition und [[Erweiterbarkeit]] von [[Modellierungssprache|Modellierungssprachen]] durch ein [[Meta-Meta-Modell]]. Unterstützt die [[Interoperabilität]] zwischen [[Tool|Tools]] und [[Standard|Standards]].
- **Abgrenzung & Grenzen:** Kein direktes [[Entwurfsmuster]] oder [[Designprinzip]], sondern ein [[Konzept]] der [[Metamodellierung]]. Nicht relevant für die [[Implementierung]] von [[Anwendung|Anwendungen]], sondern für die Definition von [[Sprache|Sprachen]] und [[Tool|Tools]].
- **Beispiel / Code:** ```text
// MOF-Schichten (M3 bis M0)
M3: Meta-Meta-Modell (MOF selbst)
M2: Meta-Modell (z. B. UML-Meta-Modell)
M1: Modell (z. B. UML-Klassendiagramm)
M0: Instanz (z. B. konkrete Objekte im System)
```
