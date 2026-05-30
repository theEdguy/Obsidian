---
id: 245da3cc-aef0-4e2c-ae59-acc194d2c509
title: "Stereotyp_(UML)"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - erweiterungsmechanismus
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Stereotyp_(UML)]]

- **Kernkonzept:** Ein [[Erweiterungsmechanismus]] in [[UML]], der es ermöglicht, bestehende [[Element|Elemente]] (z. B. [[Klasse|Klassen]], [[Assoziation|Assoziationen]]) mit zusätzlicher [[Semantik]] zu versehen, ohne das [[Meta-Modell]] zu ändern.
- **Nutzen & Zweck:** Erlaubt die [[Anpassung]] von [[UML]] an domänenspezifische [[Anforderung|Anforderungen]] oder [[Entwurfsmuster]]. Fördert die [[Wiederverwendung]] von [[Modellierungselement|Modellierungselementen]] durch [[Erweiterung]] statt [[Neudefinition]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Meta-Modell]]-Erweiterungen, sondern eine [[Lightweight-Erweiterung]]. Übermäßige Verwendung kann zu [[Unübersichtlichkeit]] führen. Sollte nur eingesetzt werden, wenn keine [[Standard|Standard]]-Elemente passen.
- **Beispiel / Code:** ```uml
<<interface>>
class MitgliedRepository {
    +findById(id: Integer): Mitglied
}

<<entity>>
class Mitglied {
    +id: Integer
    +name: String
}
```
