---
id: 3dc4b594-c896-4d88-a467-bd7dfbd7b7f0
title: "Assoziationsklasse"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Assoziationsklasse]]

- **Kernkonzept:** Eine [[Assoziationsklasse]] ist eine [[Klasse]], die einer [[Assoziation]] zugeordnet ist und [[Attribut|Attribute]] oder [[Operation|Operationen]] enthält, die weder der einen noch der anderen beteiligten [[Klasse]] eindeutig zugeordnet werden können.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung von [[Metadaten]] oder [[Verhalten]], die direkt mit der [[Beziehung]] zwischen [[Objekt|Objekten]] verbunden sind, ohne die [[Kohäsion]] der beteiligten [[Klasse|Klassen]] zu beeinträchtigen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Attribut|Attribute]] oder [[Operation|Operationen]] klar einer der beteiligten [[Klasse|Klassen]] zugeordnet werden können. In solchen Fällen sollte eine reguläre [[Klasse]] mit [[Assoziation|Assoziationen]] verwendet werden.
- **Beispiel / Code:** ```java
class MitgliedSport {
    private LocalDate seit;
    private int ranking;
    private Mitglied mitglied;
    private Sport sport;
}
```
