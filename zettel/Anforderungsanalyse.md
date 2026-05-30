---
id: ede5cb96-a7a8-4147-a7f3-53975728b72f
title: "Anforderungsanalyse"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - analyse
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Anforderungsanalyse]]

- **Kernkonzept:** Der Prozess der systematischen Erfassung, Strukturierung und Bewertung von [[Anforderung|Anforderungen]] – sowohl [[funktionale_Anforderung|funktionalen]] als auch [[nicht-funktionale_Anforderung|nicht-funktionalen]] – an ein [[Softwaresystem]]. Ziel ist die Schaffung einer konsistenten Grundlage für [[Design]], [[Implementierung]], [[Use_Case|Use-Case]]-Modellierung und [[Systemdesign]], um spätere [[Änderung|Änderungen]] oder [[Fehlentwicklung|Fehlentwicklungen]] zu vermeiden.
- **Nutzen & Zweck:** Die [[Anforderungsanalyse]] löst das Problem unklarer oder widersprüchlicher [[Zielvorgabe|Zielvorgaben]] in [[Softwareprojekt|Softwareprojekten]] durch systematische Aufbereitung der [[Problemdomäne]]. Sie stellt sicher, dass alle [[Stakeholder]]-Bedürfnisse verstanden und in [[überprüfbare_Anforderung|überprüfbare Anforderungen]] überführt werden. Dadurch wird eine klare [[Spezifikation]] für [[Implementierung]] und [[Qualitätssicherung]] geschaffen, was spätere [[Nachbesserung|Nachbesserungen]] verhindert.
- **Abgrenzung & Grenzen:** Die [[Anforderungsanalyse]] ist kein Ersatz für [[Prototyping]] oder [[Benutzerfeedback]] und sollte nicht mit der [[Implementierung]] verwechselt werden – sie beschreibt *was* das System leisten muss, nicht *wie*. Bei extrem dynamischen [[Anforderung|Anforderungen]] kann der Aufwand den Nutzen übersteigen. Im Gegensatz zu [[Ad-hoc-Entwicklung|Ad-hoc-Entwicklungen]] erfordert sie strukturierte Methoden wie [[Interview|Interviews]], [[Workshop|Workshops]] oder [[Prototyping]]. Zudem ist eine enge Zusammenarbeit mit [[Stakeholder|Stakeholdern]] essenziell.
- **Beispiel / Code:** ```plaintext
// Beispiel für strukturierte Anforderungen
Funktionale Anforderung: FR-001
Beschreibung: Das System muss neue Mitglieder erfassen.
Priorität: Hoch (sichtbar)
Akzeptanzkriterium: Ein Mitglied kann mit Name, Adresse und Beitrittsdatum angelegt werden.

Ref.# | Funktion/Constraint               | Kategorie
------|----------------------------------|----------
F1.1  | Adresse ändern                   | must
A1.1  | Zugriff nur nach Authentisierung | must
```
