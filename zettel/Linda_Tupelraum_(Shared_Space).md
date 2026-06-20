---
id: 197a883a-bb0c-51c4-ae86-cf4665044348
title: "Linda Tupelraum (Shared Space)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Architekturen"
---

# [[Linda Tupelraum (Shared Space)]]

- **Kernkonzept:** Ein referenziell und temporal entkoppeltes Koordinationsmodell auf Basis eines gemeinsamen, persistenten Datenraums (Multimenge). Operationen sind out(t) (Tupel schreiben), in(t) (Tupel lesen und entfernen; blockierend falls kein Treffer), und rd(t) (Tupel-Kopie lesen; blockierend).
- **Nutzen & Zweck:** Ein referenziell und temporal entkoppeltes Koordinationsmodell auf Basis eines gemeinsamen, persistenten Datenraums (Multimenge). Operationen sind out(t) (Tupel schreiben), in(t) (Tupel lesen und entfernen; blockierend falls kein Treffer), und rd(t) (Tupel-Kopie lesen; blockierend).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# Bob schreibt in den Tupelraum:
blog._out(("bob", "distsys", "I am studying chap 2"))
# Chuck liest blockierend mit Template:
t1 = blog._rd(("bob", "distsys", str))
```
