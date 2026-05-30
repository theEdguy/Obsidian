---
id: 7516051f-813a-46c5-9753-53e3d887b824
title: "Complete_Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - draft
source: "SWE Slides (Folien 91-105)"
---

# [[Complete_Vererbung]]

- **Kernkonzept:** [[Complete_Vererbung]] beschreibt eine [[Vererbungsbeziehung|Vererbungsbeziehung]], bei der alle möglichen [[Unterklasse|Unterklassen]] einer [[Oberklasse]] explizit modelliert sind und keine [[Instanz|Instanzen]] außerhalb dieser [[Unterklasse|Unterklassen]] existieren. Im Gegensatz dazu ermöglicht [[Incomplete_Vererbung]] die spätere Erweiterung um neue [[Unterklasse|Unterklassen]], ohne die [[Oberklasse]] zu verändern.
- **Nutzen & Zweck:** [[Complete_Vererbung]] stellt sicher, dass alle [[Variante|Varianten]] einer [[Oberklasse]] bekannt und modelliert sind, was die [[Vollständigkeit]] und [[Konsistenz]] des [[Modell]]s erhöht. Dies ist besonders nützlich für [[Enumeration|Enumerationen]] oder geschlossene [[Kategorie|Kategorien]], bei denen keine Erweiterung vorgesehen ist. [[Incomplete_Vererbung]] fördert dagegen die [[Erweiterbarkeit]] und [[Flexibilität]] des [[Entwurf]]s, indem sie die spätere Hinzufügung neuer [[Unterklasse|Unterklassen]] ohne Änderung der [[Oberklasse]] erlaubt.
- **Abgrenzung & Grenzen:** [[Complete_Vererbung]] sollte nicht genutzt werden, wenn neue [[Unterklasse|Unterklassen]] später hinzugefügt werden sollen, da sie die [[Erweiterbarkeit]] einschränkt. In solchen Fällen ist [[Incomplete_Vererbung]] vorzuziehen. Umgekehrt kann [[Incomplete_Vererbung]] zu unvollständigen oder inkonsistenten [[Modell]]en führen, wenn alle [[Variante|Varianten]] der [[Oberklasse]] bereits bekannt sind. Die Wahl zwischen beiden Ansätzen hängt von den Anforderungen an die [[Modellierung]] und die zukünftige [[Wartbarkeit]] ab.
- **Beispiel / Code:** ```java
// Complete_Vererbung: Alle Vereinsmanager sind entweder Vorstand oder Abteilungsleiter
public abstract class Vereinsmanager {}
public class Vorstand extends Vereinsmanager {}
public class Abteilungsleiter extends Vereinsmanager {}

// Incomplete_Vererbung: Weitere Mitgliedstypen (z. B. Herr, Senior) können später hinzugefügt werden
public abstract class Mitglied {}
public class Junior extends Mitglied {}
public class Dame extends Mitglied {}
```
