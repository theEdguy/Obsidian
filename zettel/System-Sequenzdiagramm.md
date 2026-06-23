---
id: 19e567a7-eb82-4c8d-a4be-8d631afa2856
title: "System-Sequenz-Diagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - anforderungsanalyse
  - modellierung
  - dynamik
  - draft
source: "software_engineering_kapitel_09"
---

# [[System-Sequenz-Diagramm]]

- **Kernkonzept:** Ein [[System-Sequenz-Diagramm]] (SSD) ist eine spezielle Form des [[Sequenzdiagramm|Sequenzdiagramms]], das die [[Interaktion]] zwischen einem [[Akteur|Akteuren]] und dem [[System]] in einer zeitlichen [[Ablauf|Abfolge]] darstellt. Es zeigt, wie [[Systemoperation|Systemoperationen]] durch [[Nachricht|Nachrichten]] (z. B. Methodenaufrufe) ausgelöst und verarbeitet werden, um einen [[Anwendungsfall|Anwendungsfall]] abzubilden, ohne interne [[Komponente|Komponenten]] oder [[Objekt|Objekte]] zu berücksichtigen.
- **Nutzen & Zweck:** Das [[System-Sequenz-Diagramm]] dient der Modellierung von [[Anwendungsfall|Anwendungsfällen]] aus der Perspektive des [[Akteur|Akteurs]], um die [[Schnittstelle|Schnittstellen]] und [[Operation|Operationen]] des [[System|Systems]] zu definieren und [[Anforderung|Anforderungen]] zu klären. Es löst das Problem, dass [[Anforderung|Anforderungen]] und [[Ablauf|Abläufe]] oft unklar oder implizit bleiben, indem es die [[Kommunikation]] zwischen [[Akteur|Akteuren]] und [[System]] strukturiert und sichtbar macht. Dadurch wird die Grundlage für die spätere [[Implementierung]] und das [[Design]] der [[Schnittstelle|Systemschnittstellen]] geschaffen, was die [[Kohäsion]] und [[Modularität]] des [[System|Systems]] fördert.
- **Abgrenzung & Grenzen:** Ein [[System-Sequenz-Diagramm]] sollte nicht genutzt werden, um interne [[Ablauf|Abläufe]] innerhalb des [[System|Systems]] oder komplexe [[Interaktion|Interaktionen]] zwischen [[Komponente|Komponenten]] oder [[Objekt|Objekten]] darzustellen – hierfür eignen sich [[Sequenzdiagramm|Sequenzdiagramme]] auf [[Objekt|Objektebene]] besser. Im Gegensatz zu [[Aktivitätsdiagramm|Aktivitätsdiagrammen]], die den [[Kontrollfluss]] und parallele [[Prozess|Prozesse]] abbilden, fokussiert sich das SSD auf die sequenzielle [[Ablauf|Abfolge]] von [[Systemoperation|Systemoperationen]] und deren Auslöser. Es ist zudem ungeeignet für die Modellierung von nicht-funktionalen [[Anforderung|Anforderungen]] (z. B. [[Performance]], [[Sicherheit]]) oder statischen [[Systemstruktur|Systemstrukturen]] (z. B. [[Klassenmodell|Klassenmodelle]]).
- **Beispiel / Code:** ```plantuml
@startuml
actor [[Akteur|Vereinsmanager]]
participant "[[System]]" as System

[[Akteur|Vereinsmanager]] -> System: mitgliedHinzufügen(name, abteilung)
alt Erfolg
    System --> [[Akteur|Vereinsmanager]]: Bestätigung
else Fehler
    System --> [[Akteur|Vereinsmanager]]: Fehlermeldung
end
@enduml
```

*Beispiel:* Ein [[Akteur|Vereinsmanager]] löst die [[Systemoperation]] `mitgliedHinzufügen` aus. Das [[System]] reagiert mit einer Bestätigung oder einer Fehlermeldung, falls das [[Mitglied]] bereits existiert. Alternativ kann auch das einfachere UML-Format verwendet werden:

```uml
:Akteur -> [[System]]: Systemoperation(parameter)
[[System]] -> Akteur: Antwort()
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Use-Case-basierte_Analyse]]
- **Folgezettel / Unterzettel:**
  - [[Interaktionsfragment]]
  - [[Lebenslinie]]
  - [[Nachricht]]
- **Querverweise:**
  - [[UML]]
  - [[Dynamische_Modellierung]]
