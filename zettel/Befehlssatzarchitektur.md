---
id: 586cf1d8-c3dd-41bb-b064-db60e1bc02f5
title: "Befehlssatzarchitektur"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - prozessor
  - virtualisierung
  - hardware
  - abstraktion
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Befehlssatzarchitektur]]

- **Kernkonzept:** Die Befehlssatzarchitektur (engl. [[Instruction Set Architecture|ISA]]) definiert die Schnittstelle zwischen [[Hardware]] und [[Software]], indem sie die Menge aller [[Maschinenbefehl|Maschinenbefehle]] festlegt, die ein [[Prozessor]] ausführen kann. Sie unterteilt sich in privilegierte [[Befehl|Befehle]] (nur für das [[Betriebssystem]]) und generelle [[Befehl|Befehle]] (für Anwendungsprogramme).
- **Nutzen & Zweck:** Sie ermöglicht die [[Abstraktion]] von [[Hardware]]-Details, sodass [[Software]] unabhängig von spezifischen [[Prozessor]]-Implementierungen entwickelt werden kann. Dies löst das Problem der [[Portierbarkeit]] und vereinfacht die [[Virtualisierung]] von Systemen, indem sie eine stabile Schnittstelle für [[Code]]-Migration und [[Isolation]] bietet.
- **Abgrenzung & Grenzen:** Nicht geeignet für Anwendungen, die direkte [[Hardware]]-Manipulation erfordern (z. B. Treiberentwicklung), da die [[Abstraktion]] Leistungseinbußen verursachen kann. Alternativen wie [[Mikroarchitektur]] oder [[Hardware]]-Beschleunigung bieten mehr Kontrolle, sind aber weniger portabel. Die [[Befehlssatzarchitektur]] unterscheidet sich von [[API]]s oder [[Systemaufruf|Systemaufrufen]], da sie auf [[Maschinenebene]] operiert.
- **Beispiel / Code:** Ein einfacher [[Befehl]] in x86-Architektur:
```asm
MOV EAX, 5  ; Lade den Wert 5 in das Register EAX
ADD EAX, 3  ; Addiere 3 zum Wert in EAX (Ergebnis: 8)
```
Dies zeigt generelle [[Befehl|Befehle]], die von jedem Programm genutzt werden können. Privilegierte [[Befehl|Befehle]] wie `HLT` (Prozessor anhalten) dürfen nur im [[Kernelmodus]] ausgeführt werden.
