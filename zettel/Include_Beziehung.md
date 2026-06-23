---
id: 7294aab4-d77d-4ec2-920d-ab728eea6fa0
title: "Include_Beziehung"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - requirements_engineering
  - use_case_modeling
  - wiederverwendung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Include_Beziehung]]

- **Kernkonzept:** Die <<include>>-Beziehung in [[Use-Case-Diagramm|Use-Case-Diagrammen]] zeigt an, dass ein [[Use_Case|Use Case]] (der *inkludierende* [[Use_Case]]) einen anderen [[Use_Case]] (den *inkludierten* [[Use_Case]]) zwingend als Teil seines [[Ablauf|Ablaufs]] einbindet, um redundante [[Ablauf|Abläufe]] zu vermeiden und die [[Wiederverwendbarkeit]] von [[Funktionalität|Funktionalitäten]] zu fördern. Die Aktionen des eingebundenen [[Use_Case|Use Cases]] werden dabei vollständig und als Ganzes im [[Basis-Use-Case|Basis-Use-Case]] ausgeführt.
- **Nutzen & Zweck:** Die [[Include-Beziehung]] vermeidet [[Redundanz]] in der [[Beschreibung]] von [[Use_Case|Use-Cases]], indem gemeinsame [[Teilablauf|Teilabläufe]] (z. B. [[Authentisierung]] oder [[Datenvalidierung]]) in separate [[Use_Case|Use-Cases]] ausgelagert werden. Dadurch wird die [[Wartbarkeit]] verbessert, die [[Konsistenz]] der [[Anforderung|Anforderungen]] sichergestellt und das [[Problem]] der Wiederholung großer, eigenständiger [[Ablauf|Abläufe]] in mehreren [[Use_Case|Use-Cases]] gelöst. Sie fördert zudem die [[Modularität]] und [[Kohäsion]] im [[Anforderungsmodell]] und ermöglicht eine effizientere [[Modellierung]], da Änderungen am eingebundenen [[Use_Case]] automatisch in allen referenzierenden [[Use_Case|Use-Cases]] wirken.
- **Abgrenzung & Grenzen:** Im Gegensatz zur [[Extend-Beziehung]] ist die Einbindung des inkludierten [[Use_Case|Use-Cases]] *obligatorisch* – er wird immer ausgeführt und stellt keine [[optionale_Funktionalität|optionale Funktionalität]] dar. Die [[Include-Beziehung]] sollte nicht für [[Variation|Variationen]] eines [[Basis-Use-Case|Basis-Use-Cases]] oder zeitliche [[Ablauf|Abläufe]] verwendet werden, da [[Use-Case-Diagramm|Use-Case-Diagramme]] keine [[Sequenz]] abbilden. Zudem vererbt die [[Include-Beziehung]] keine [[Beziehung|Beziehungen]] zu [[Akteur|Akteuren]]; diese müssen explizit modelliert werden. Sie eignet sich nicht für triviale oder zu kleine [[Teilablauf|Teilabläufe]], da dies die [[Übersichtlichkeit]] des [[Modell|Modells]] beeinträchtigen kann. Im Gegensatz zur [[Generalisierung]] (Vererbung) wird keine [[Spezialisierung]] oder [[Erweiterung]] des [[Verhalten|Verhaltens]] erreicht.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor [[Vereinsmanager]]

usecase "[[Mitglieder_verwalten]]" as UC1
usecase "[[Authentisierung]]" as UC2
usecase "[[Daten_validieren]]" as UC3

[[Vereinsmanager]] --> UC1
UC1 --> UC2 : <<include>>
UC1 --> UC3 : <<include>>
@enduml
```

*Erläuterung:* Der [[Use_Case]] „[[Mitglieder_verwalten]]“ bindet die [[Use_Case|Use-Cases]] „[[Authentisierung]]“ und „[[Daten_validieren]]“ zwingend ein, da jede [[Mitgliederverwaltung]] eine [[Authentisierung]] und [[Datenvalidierung]] erfordert. Beide [[Teilablauf|Teilabläufe]] sind keine eigenständigen [[Anwendungsfall|Anwendungsfälle]], sondern wiederverwendbare [[Funktionalität|Funktionalitäten]].

Ein weiteres Beispiel in textueller UML-Notation:

```plaintext
[[Bestellung_aufgeben]] --> [[Zahlung_abwickeln]] : <<include>>
```

Hier ist die [[Zahlung_abwickeln|Zahlungsabwicklung]] ein obligatorischer [[Teilablauf]] der [[Bestellung_aufgeben|Bestellabwicklung]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[Use_Case_Beziehungen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Beziehungen]]
  - [[Wiederverwendung]]
