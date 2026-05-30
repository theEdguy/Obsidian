---
id: 09401c53-745f-4374-a481-978ad0341fc4
title: "UML_Instanzdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - softwarearchitektur
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[UML_Instanzdiagramm]]

- **Kernkonzept:** Ein [[Diagrammtyp]] der [[UML]], der konkrete [[Instanz|Instanzen]] von [[Klasse|Klassen]] und deren [[Beziehung|Beziehungen]] zur [[Laufzeit]] darstellt. Zeigt [[Objekt|Objekte]] mit ihren aktuellen [[Attributwert|Attributwerten]].
- **Nutzen & Zweck:** Hilft, die dynamische [[Struktur]] eines [[System|Systems]] zur [[Laufzeit]] zu verstehen und zu [[Dokumentation|dokumentieren]]. Nützlich für die [[Fehlersuche]] und das Verständnis komplexer [[Objektgraph|Objektgraphen]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[UML_Klassendiagramm|Klassendiagramme]], da es keine [[Klasse|Klassen]]-Struktur zeigt. Beschränkt auf die Darstellung statischer [[Momentaufnahme|Momentaufnahmen]], nicht für [[Verhalten]] geeignet.
- **Beispiel / Code:** ```uml
object :Spieler {
    name = "Max Mustermann"
    nummer = 10
}

object :Mitglied {
    name = "Erika Beispiel"
}

:Mitglied -- :Spieler
```
