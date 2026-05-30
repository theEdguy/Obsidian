---
id: ae46a368-8313-42ef-a473-ae7566982bee
title: "Assoziation_und_Attribut"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Assoziation_und_Attribut]]

- **Kernkonzept:** [[Attribut|Attribute]] einer [[Klasse]] können als nicht navigierbare [[Aggregation|Aggregationen]] (oder [[Komposition|Kompositionen]]) modelliert werden, um die [[Semantik]] der [[Beziehung]] explizit darzustellen.
- **Nutzen & Zweck:** Sie ermöglicht eine klarere [[Modellierung]] von [[Datenstruktur|Datenstrukturen]], indem [[Attribut|Attribute]] als eigenständige [[Klasse|Klassen]] mit [[Assoziation|Assoziationen]] dargestellt werden, was die [[Erweiterbarkeit]] und [[Wartbarkeit]] verbessert.
- **Abgrenzung & Grenzen:** Nicht sinnvoll, wenn die [[Attribut|Attribute]] trivial sind oder keine zusätzliche [[Semantik]] oder [[Verhalten]] benötigen. Kann die [[Modellkomplexität]] unnötig erhöhen.
- **Beispiel / Code:** ```java
class Mitglied {
    private Anschrift adresse;
    // Statt: private String adresse;
}
```
