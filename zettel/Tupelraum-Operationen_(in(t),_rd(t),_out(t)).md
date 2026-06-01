---
id: 4e1fefb1-c9c5-4619-8a7c-ea5a37bc3ab3
title: "Tupelraum-Operationen (in(t), rd(t), out(t))"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - koordination
  - tupelraum
  - linda
  - middleware
  - parallelität
  - mustervergleich
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Tupelraum-Operationen (in(t), rd(t), out(t))]]

- **Kernkonzept:** Ein [[Tupelraum|Tupelraum]] ist ein gemeinsamer [[Speicher|Speicherbereich]] für [[Tupel|Tupel]], der durch drei grundlegende [[Operation|Operationen]] manipuliert wird: `in(t)` entfernt ein passendes [[Tupel]], `rd(t)` liest es nicht-destruktiv, und `out(t)` fügt ein [[Tupel]] hinzu. Die [[Operation|Operationen]] ermöglichen asynchrone [[Koordination]] in [[Verteilte Systeme|verteilten Systemen]].
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der losen [[Kopplung]] und [[Synchronisation]] in [[Verteilte Systeme|verteilten Systemen]], indem es einen [[Mustervergleich|musterbasierten]] Zugriff auf [[Daten]] ohne direkte [[Kommunikation]] zwischen [[Prozess|Prozessen]] ermöglicht. Es vereinfacht die [[Implementierung]] von [[Parallelität]] und [[Koordination]] ohne explizite [[Locks]] oder [[Nachrichten]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]] mit strengen [[Echtzeitanforderung|Echtzeitanforderungen]] oder deterministischen [[Zugriffsmuster|Zugriffsmustern]], da `in(t)` und `rd(t)` blockieren können. Im Vergleich zu [[Message-Passing]] oder [[Shared Memory]] bietet es weniger [[Kontrolle]] über [[Latenz]] und [[Reihenfolge]]. Alternativen wie [[Publish-Subscribe]] sind effizienter für [[Ereignis]]-basierte [[Kommunikation]].
- **Beispiel / Code:** ```python
# Beispiel: Linda-Tupelraum in Python-ähnlicher Syntax
blog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]

# Bob fügt Tupel hinzu
blog._out(("bob", "distsys", "I am studying chap 2"))
blog._out(("bob", "gtcn", "Cool book!"))

# Chuck liest Tupel nicht-destruktiv
t1 = blog._rd(("bob", "distsys", str))

# Alice entfernt ein Tupel
t2 = blog._in(("alice", "gtcn", str))
```
