---
id: 372b004f-4365-4472-ac1f-68ec248e36ce
title: "Fragment_in_Sequenzdiagrammen"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - kontrollstruktur
  - modellierung
  - nebenläufigkeit
  - draft
source: "SWE Slides (Folien 301-315)"
---

# [[Fragment_in_Sequenzdiagrammen]]

- **Kernkonzept:** Ein [[Fragment_in_Sequenzdiagrammen|Fragment]] strukturiert [[Sequenzdiagramm|Sequenzdiagramme]] durch spezielle [[Kontrollstruktur|Kontrollstrukturen]] wie [[Schleife|Schleifen]], [[Alternative|Alternativen]], [[Parallelität|parallele Abläufe]] oder [[Nebenläufigkeit|nebenläufige Interaktionen]]. Es ermöglicht die präzise Modellierung komplexer [[Ablauf|Abläufe]] und [[Kontrollfluss|Kontrollflüsse]] innerhalb eines Diagramms.
- **Nutzen & Zweck:** Fragmente erlauben die Darstellung von [[Kontrollfluss|Kontrollflüssen]] wie [[Bedingung|Bedingungen]], [[Iteration|Iterationen]], [[Nebenläufigkeit|Nebenläufigkeit]] oder [[Parallelität|parallelen Prozessen]] in [[Sequenzdiagramm|Sequenzdiagrammen]], ohne die Lesbarkeit zu beeinträchtigen. Sie reduzieren die Komplexität durch Modularisierung und unterstützen die Modellierung von [[Multithreading|multithreaded]] [[System|Systemen]] oder gleichzeitiger Verarbeitung mehrerer [[Anfrage|Anfragen]].
- **Abgrenzung & Grenzen:** Nicht alle [[Fragment_in_Sequenzdiagrammen|Fragmente]] sind für einfache [[Ablauf|Abläufe]] sinnvoll. Übermäßige Nutzung kann die Verständlichkeit erschweren, insbesondere wenn [[Nebenläufigkeit|Nebenläufigkeit]] oder [[Kontrollstruktur|Kontrollstrukturen]] nicht erforderlich sind. Für streng sequenzielle [[Interaktion|Interaktionen]] reichen oft [[Nachricht|Nachrichten]] ohne Fragmente aus. Zudem erhöht die Darstellung von [[Parallelität|Parallelität]] die Komplexität, wenn sie nicht zwingend benötigt wird.
- **Beispiel / Code:** ```uml
alt [Bedingung 1]
    :Objekt1 -> Objekt2: Nachricht A
[else]
    :Objekt1 -> Objekt2: Nachricht B
end
```

```uml
par
    :System -> MemberField: getMember()
    :System -> DepartmentField: getDepartment()
end
```
