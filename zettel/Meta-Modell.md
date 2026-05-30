---
id: 8d589783-3c03-438f-9721-cae9d08f0961
title: "Meta-Modell"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - metamodellierung
  - uml
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Meta-Modell]]

- **Kernkonzept:** Ein [[Modell]], das die [[Struktur]] und [[Regel|Regeln]] einer [[Modellierungssprache]] (z. B. [[UML]]) definiert. Beschreibt, welche [[Element|Elemente]] (z. B. [[Klasse|Klassen]], [[Attribut|Attribute]], [[Assoziation|Assoziationen]]) existieren und wie sie zusammenhängen.
- **Nutzen & Zweck:** Ermöglicht die formale Definition von [[Modellierungssprache|Modellierungssprachen]] und deren [[Erweiterbarkeit]]. Dient als Grundlage für [[Tool|Tools]] wie [[UML]]-Editoren und [[Code-Generator|Code-Generatoren]].
- **Abgrenzung & Grenzen:** Kein direktes [[Entwurfsmuster]] oder [[Designprinzip]], sondern ein [[Konzept]] der [[Metamodellierung]]. Nicht relevant für die direkte [[Implementierung]] von [[Software]], sondern für die Definition von [[Sprache|Sprachen]] und [[Tool|Tools]].
- **Beispiel / Code:** ```uml
// Ausschnitt aus einem UML-Meta-Modell
class Class {
    +name: String
    +attributes: Attribute[*]
    +operations: Operation[*]
}

class Attribute {
    +name: String
    +type: Classifier
}
```
