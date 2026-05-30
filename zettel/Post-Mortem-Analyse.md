---
id: 4c36d7e5-8083-45d9-9da8-8c8b42b65153
title: "Post-Mortem-Analyse"
date: 2026-05-30
tags:
  - software_engineering
  - prozess
  - methode
  - projektmanagement
  - qualitätssicherung
  - draft
source: "SWE Slides (Folien 16-30)"
---

# [[Post-Mortem-Analyse]]

- **Kernkonzept:** Eine [[retrospektive_Methode|retrospektive Methode]], bei der ein abgeschlossenes [[Software-Projekt|Software-Projekt]] oder [[Meilenstein|Meilenstein]] analysiert wird, um [[Erfolg|Erfolge]], [[Fehler]], [[Lessons_Learned|Lessons Learned]] und [[Erfolgsfaktor|Erfolgsfaktoren]] zu identifizieren. Ziel ist die systematische [[Reflexion]] über [[Erfahrung|Erfahrungen]], um zukünftige [[Projektmanagement|Projektmanagement]]-Prozesse zu verbessern.
- **Nutzen & Zweck:** Fördert die [[kontinuierliche_Verbesserung]] von [[Prozess|Prozessen]] und [[Methode|Methoden]] durch die Identifikation von [[Risiko|Risiken]] und [[Erfolgsfaktor|Erfolgsfaktoren]] in [[Software-Entwicklungsprozess|Software-Entwicklungsprozessen]]. Unterstützt die [[Qualitätssicherung]] und das [[Risikomanagement]], indem es [[Lessons_Learned|Lessons Learned]] dokumentiert und für zukünftige [[Projekt|Projekte]] nutzbar macht. Trägt zur Stärkung von [[Offenheit]] und [[Vertrauen]] im [[Team]] bei, sofern konstruktiv durchgeführt.
- **Abgrenzung & Grenzen:** Keine [[Echtzeit-Analyse]]; Ergebnisse sind rückblickend und können durch subjektive Wahrnehmungen verzerrt sein. Eignet sich nicht zur aktiven Steuerung laufender [[Projekt|Projekte]], hier sind [[Meilenstein|Meilensteine]] oder [[Agile_Methodik|agile Retrospektiven]] besser geeignet. Kann zu [[Schuldzuweisung|Schuldzuweisungen]] führen, wenn die Durchführung nicht auf [[konstruktive_Kritik]] und [[Lösungsorientierung]] ausgerichtet ist.
- **Beispiel / Code:** ```markdown
# Beispiel: Post-Mortem-Analyse eines gescheiterten [[Software-Projekt|Software-Projekts]]

## Kontext
- Projekt: Entwicklung einer [[Kundenportal|Kundenportal]]-Anwendung
- Dauer: 6 Monate
- Teamgröße: 8 [[Entwickler|Mitglieder]]

## Identifizierte Probleme
- [[Anforderung|Anforderungen]] waren unklar und änderten sich häufig (fehlende [[Stakeholder|Stakeholder]]-Einbindung)
- [[Aufwandsschätzung|Aufwandsschätzungen]] waren unrealistisch (keine historische Datenbasis)
- Mangelnde [[Testabdeckung]] führte zu späten [[Bug|Bugs]] in der [[Produktivumgebung]]

## Lessons Learned
- Frühere und regelmäßige Einbindung von [[Stakeholder|Stakeholdern]] reduziert [[Anforderungsänderung|Anforderungsänderungen]]
- [[User_Story|User Stories]] und [[Backlog]]-Priorisierung verbessern die [[Aufwandsschätzung|Aufwandsschätzung]]
- Automatisierte [[Test|Tests]] (z. B. [[Unit_Test|Unit-Tests]], [[Integrationstest|Integrationstests]]) erhöhen die [[Codequalität]]

## Maßnahmen für zukünftige Projekte
- Einführung von [[Sprint_Review|Sprint Reviews]] zur kontinuierlichen [[Feedback|Feedback]]-Einholung
- Nutzung von [[Story_Point|Story Points]] für realistischere [[Aufwandsschätzung|Aufwandsschätzungen]]
- Implementierung einer [[CI/CD-Pipeline]] zur frühzeitigen Erkennung von [[Bug|Bugs]]
```
