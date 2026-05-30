---
id: cdc49a8c-a9e2-47e2-847d-5e4a678cf7be
title: "Stereotype"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - erweiterung
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Stereotype]]

- **Kernkonzept:** Ein [[Stereotype]] ist eine Erweiterung des [[Meta-Modell]]s, um eigene [[Modellelement|Modellelemente]] mit domänenspezifischen [[Eigenschaft|Eigenschaften]] und [[Bedingung|Bedingungen]] zu definieren. Es wird in [[UML]] verwendet, um [[Klasse|Klassen]] oder [[Beziehung|Beziehungen]] zu annotieren.
- **Nutzen & Zweck:** Es ermöglicht die Anpassung der [[Modellierungssprache]] an spezifische [[Domäne|Domänen]] oder [[Anforderung|Anforderungen]], z. B. für [[Persistenz]], [[Sicherheit]] oder [[Verteilung]]. Dies erhöht die [[Ausdrucksstärke]] des [[Modell]]s.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn keine domänenspezifischen Erweiterungen benötigt werden. Übermäßige [[Stereotype|Stereotypen]] können die [[Komplexität]] des [[Modell]]s erhöhen und die [[Lesbarkeit]] beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel für einen Stereotypen <<persistent>>
@Persistent(tableName = "Mitglied")
public class Mitglied {
    private String name;
}
```
