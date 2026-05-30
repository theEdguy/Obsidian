---
id: 9a0b76c1-f293-429a-9c99-c3e14c4b4fe4
title: "Include_Beziehung"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - requirements_engineering
  - use_case_modeling
  - draft
source: "SWE Slides (Folien 166-180)"
---

# [[Include_Beziehung]]

- **Kernkonzept:** Die <<include>>-Beziehung in [[Use-Case-Diagramm|Use-Case-Diagrammen]] zeigt an, dass ein [[Use_Case|Use Case]] (der *inkludierende* [[Use_Case]]) einen anderen [[Use_Case]] (den *inkludierten* [[Use_Case]]) zwingend als Teil seines [[Ablauf|Ablaufs]] einbindet, um redundante [[Ablauf|Abläufe]] zu vermeiden und die [[Wiederverwendbarkeit]] von [[Funktionalität|Funktionalitäten]] zu fördern.
- **Nutzen & Zweck:** Die [[Include-Beziehung]] vermeidet [[Redundanz]] in der [[Beschreibung]] von [[Use_Case|Use-Cases]], indem gemeinsame [[Teilablauf|Teilabläufe]] (z. B. [[Authentisierung]]) in separate [[Use_Case|Use-Cases]] ausgelagert werden. Dadurch wird die [[Wartbarkeit]] verbessert und das [[Problem]] der Wiederholung großer, eigenständiger [[Ablauf|Abläufe]] in mehreren [[Use_Case|Use-Cases]] gelöst. Sie fördert zudem die [[Modularität]] und [[Kohäsion]] im [[Anforderungsmodell]].
- **Abgrenzung & Grenzen:** Im Gegensatz zur [[Extend-Beziehung]] ist die Einbindung des inkludierten [[Use_Case|Use-Cases]] *obligatorisch* – er wird immer ausgeführt. Die [[Include-Beziehung]] sollte nicht für [[optionale_Funktionalität|optionale Funktionalitäten]] oder [[Variation|Variationen]] eines [[Basis-Use-Case|Basis-Use-Cases]] verwendet werden, da hier die [[Extend-Beziehung]] vorzuziehen ist. Sie stellt keine zeitliche Abfolge dar und vererbt keine [[Beziehung|Beziehungen]] zu [[Akteur|Akteuren]].
- **Beispiel / Code:** ```plantuml
@startuml
[[Mitglieder_verwalten]] --> [[Authentisierung]] : <<include>>
@enduml
```

Hier wird der [[Use_Case]] „[[Authentisierung]]“ zwingend in den [[Use_Case]] „[[Mitglieder_verwalten]]“ eingebunden. Ein weiteres Beispiel in UML-Notation:

```plaintext
[[Bestellung_aufgeben]] --> [[Zahlung_abwickeln]] : <<include>>
```

In diesem Fall ist die [[Zahlung_abwickeln|Zahlungsabwicklung]] ein obligatorischer [[Teilablauf]] der [[Bestellung_aufgeben|Bestellabwicklung]].
