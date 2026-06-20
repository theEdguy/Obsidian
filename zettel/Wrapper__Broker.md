---
id: 68585145-8707-5972-b11b-f97c716474de
title: "Wrapper / Broker"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Architekturen"
---

# [[Wrapper / Broker]]

- **Kernkonzept:** Entwurfsmuster zur Integration von Altsystemen (Legacy). Ein Wrapper/Adapter übersetzt Client-Aufrufe in die Legacy-Schnittstelle. Um quadratische Komplexität bei N Systemen zu vermeiden (O(N^2) für 1-zu-1 Wrapper), vermittelt ein Broker die Aufrufe, was die Komplexität auf O(N) reduziert (2N Wrapper).
- **Nutzen & Zweck:** Entwurfsmuster zur Integration von Altsystemen (Legacy). Ein Wrapper/Adapter übersetzt Client-Aufrufe in die Legacy-Schnittstelle. Um quadratische Komplexität bei N Systemen zu vermeiden (O(N^2) für 1-zu-1 Wrapper), vermittelt ein Broker die Aufrufe, was die Komplexität auf O(N) reduziert (2N Wrapper).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
