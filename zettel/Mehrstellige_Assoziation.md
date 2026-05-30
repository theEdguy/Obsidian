---
id: 90758789-4bd9-4ed3-a900-63ad1905bc3d
title: "Mehrstellige_Assoziation"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Mehrstellige_Assoziation]]

- **Kernkonzept:** Eine [[Mehrstellige_Assoziation|mehrstellige Assoziation]] beschreibt eine [[Beziehung]] zwischen drei oder mehr [[Klasse|Klassen]], wobei jede [[Instanz]] der [[Assoziation]] eine Kombination von [[Instanz|Instanzen]] der beteiligten [[Klasse|Klassen]] verbindet.
- **Nutzen & Zweck:** Sie ermöglicht die Modellierung komplexer [[Beziehung|Beziehungen]], die nicht durch [[Binäre_Assoziation|binäre Assoziationen]] abgebildet werden können, z. B. in [[Datenbankmodellierung|Datenbankmodellen]] oder [[Geschäftsprozessmodellierung|Geschäftsprozessen]].
- **Abgrenzung & Grenzen:** Übermäßig komplex und schwer verständlich, wenn die [[Beziehung]] durch mehrere [[Binäre_Assoziation|binäre Assoziationen]] oder [[Assoziationsklasse|Assoziationsklassen]] einfacher dargestellt werden kann. Sollte nur bei zwingender Notwendigkeit eingesetzt werden.
- **Beispiel / Code:** ```java
class Wettkampf {
    private Team teamA;
    private Team teamB;
    private Durchgang ersteRunde;
    private Durchgang zweiteRunde;
}
```
