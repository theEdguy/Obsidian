---
id: abe846aa-3338-4040-b1bf-3e7fee7e66e0
title: "Generelle Instruktionen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - virtualisierung
  - befehlssatzarchitektur
  - hardware
  - betriebssysteme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Generelle Instruktionen]]

- **Kernkonzept:** Generelle [[Instruktion|Instruktionen]] sind eine Untermenge der [[Befehlssatzarchitektur]], die von jedem [[Programm]] ausgeführt werden können, ohne spezielle [[Berechtigung|Berechtigungen]] des [[Betriebssystem|Betriebssystems]] zu benötigen.
- **Nutzen & Zweck:** Sie ermöglichen die Ausführung von [[Anwendungscode]] direkt auf der [[Hardware]] oder in [[virtualisierten Umgebungen]], ohne dass [[privilegierte Instruktionen]] oder [[Systemaufruf|Systemaufrufe]] erforderlich sind. Dies vereinfacht die [[Portierbarkeit]] von [[Software]] und unterstützt die [[Isolation]] in [[verteilten Systemen]].
- **Abgrenzung & Grenzen:** Generelle [[Instruktion|Instruktionen]] dürfen nicht für sicherheitskritische Operationen genutzt werden, da sie keine [[Berechtigungsprüfung]] durch das [[Betriebssystem]] erfordern. Im Gegensatz zu [[privilegierten Instruktionen]] können sie nicht für [[Hardware]]-nahe Steuerung oder [[Ressourcenverwaltung]] verwendet werden. Für solche Aufgaben sind [[Systemaufruf|Systemaufrufe]] oder [[Kernel]]-Modus-Operationen notwendig.
- **Beispiel / Code:** Ein einfaches Beispiel für generelle Instruktionen ist die Addition zweier Registerwerte in Assembler:

```asm
ADD R1, R2, R3  ; Addiere den Wert in R2 zu R3 und speichere das Ergebnis in R1
```

Diese Instruktion kann von jedem [[Programm]] ausgeführt werden, ohne dass das [[Betriebssystem]] eingreifen muss.
