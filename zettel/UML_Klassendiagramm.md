---
aliases:
- Klassendiagramm
date: 2026-05-30
id: 1805e285-6110-4acc-b33d-6ddf3253a807
source: SWE Slides (Folien 76-90)
tags:
- software_engineering
- uml
- modellierung
- softwarearchitektur
- draft
title: UML_Klassendiagramm
---

# [[UML_Klassendiagramm]]

- **Kernkonzept:** Ein [[Diagrammtyp]] der [[UML]], der die [[Struktur]] eines [[System|Systems]] durch [[Klasse|Klassen]], deren [[Attribut|Attribute]], [[Operation|Operationen]] und [[Beziehung|Beziehungen]] (z. B. [[Vererbung_(OOP)|Vererbung]], [[Assoziation]]) darstellt.
- **Nutzen & Zweck:** Dient der visuellen [[Modellierung]] von [[Software]]-Architekturen und fördert die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]]. Unterstützt die [[Dokumentation]] und [[Analyse]] von [[System|Systemen]] im [[Entwurfsprozess]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Code]], sondern ein [[Werkzeug]] zur [[Abstraktion]] und [[Kommunikation]]. Nicht geeignet für die Darstellung dynamischer [[Aspekt|Aspekte]] (z. B. [[Verhalten]]), hierfür sind [[UML_Sequenzdiagramm|Sequenzdiagramme]] oder [[UML_Aktivitätsdiagramm|Aktivitätsdiagramme]] besser geeignet.
- **Beispiel / Code:** ```uml
class Mitglied {
    +name: String
    +adresse: String
    +leistungsprognose(datum: Date): Integer
}

class Spieler {
    -nummer: Integer
    +vorstellen()
}

Mitglied <|-- Spieler
```
