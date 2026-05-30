---
id: 78527529-cee8-4646-9b99-2f123ac2a354
title: "History-Zustand"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - systemmodellierung
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[History-Zustand]]

- **Kernkonzept:** Ein [[History-Zustand]] ist ein spezieller [[Zustand]] in einem [[Zustandsdiagramm]], der sich den zuletzt aktiven [[Unterzustand]] eines [[Zusammengesetzter_Zustand|zusammengesetzten Zustands]] merkt. Er ermöglicht die Rückkehr zu diesem [[Unterzustand]] nach einem temporären Verlassen.
- **Nutzen & Zweck:** Er ermöglicht die Wiederaufnahme eines [[Zustand|Zustands]] nach einer Unterbrechung, ohne den gesamten [[Zustand]] neu aufbauen zu müssen. Dies ist nützlich in [[System|Systemen]] mit unterbrechbaren [[Ablauf|Abläufen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[System|Systeme]], bei denen die [[Zustand|Zustände]] keine Unterbrechungen zulassen oder keine hierarchische Struktur aufweisen. Alternativen sind explizite [[Zustand|Zustandsübergänge]] oder [[Stack-basierte_Zustandsverwaltung]].
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> A
    state A {
        [*] --> Z1
        Z1 --> Z2: e
        Z2 --> Z1: e
        --
        H: History
    }
    A --> B: ex
    B --> A: e
    A --> [*]: ex
```
