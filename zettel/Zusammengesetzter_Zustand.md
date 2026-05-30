---
id: 1dfdc542-7570-437f-bb88-716bbe5e027c
title: "Zusammengesetzter_Zustand"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - systemmodellierung
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Zusammengesetzter_Zustand]]

- **Kernkonzept:** Ein [[Zusammengesetzter_Zustand]] ist ein [[Zustand]] in einem [[Zustandsdiagramm]], der aus mehreren [[Unterzustand|Unterzuständen]] besteht. Er ermöglicht die Modellierung von [[Zustand|Zuständen]] unterschiedlicher Granularität.
- **Nutzen & Zweck:** Er reduziert die [[Komplexität]] von [[Zustandsdiagramm|Zustandsdiagrammen]], indem er [[Zustand|Zustände]] hierarchisch strukturiert. Dies ist besonders nützlich für [[System|Systeme]] mit vielen [[Zustand|Zuständen]] oder verschachtelten [[Verhalten|Verhaltensmustern]].
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[System|Systeme]] mit wenigen [[Zustand|Zuständen]], da die Hierarchie die [[Modellierung]] unnötig verkompliziert. Alternativen sind flache [[Zustandsdiagramm|Zustandsdiagramme]] oder [[Aktivitätsdiagramm|Aktivitätsdiagramme]].
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> Aktiv
    state Aktiv {
        [*] --> Wählen
        Wählen --> Verbunden: [Gegenstelle nimmt an]
        Verbunden --> Wählen: auflegen
    }
    Aktiv --> Inaktiv: auflegen
```
