---
id: 7709118d-616a-4a2a-b92c-b78642e3f1dc
title: "Multimenge (im Kontext von Tupelräumen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - tupelraum
  - koordination
  - nebenläufigkeit
  - datenstrukturen
  - publish-subscribe
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Multimenge (im Kontext von Tupelräumen)]]

- **Kernkonzept:** Eine [[Multimenge|Multimenge]] im [[Tupelraum|Tupelraum]]-Kontext ermöglicht das mehrfache Speichern identischer [[Tupel|Tupel]], wodurch eine flexible [[Datenstruktur|Datenstruktur]] für verteilte [[Koordination|Koordinationen]] entsteht.
- **Nutzen & Zweck:** Sie löst das Problem der [[Mehrfachnutzung|Mehrfachnutzungen]] identischer [[Daten|Daten]] in verteilten Systemen, indem sie [[Duplikate|Duplikate]] erlaubt und so [[Nebenläufigkeit|nebenläufige]] [[Operationen|Operationen]] wie `out(t)`, `in(t)` und `rd(t)` unterstützt. Dies vereinfacht die [[Synchronisation|Synchronisation]] in [[Publish-Subscribe-Architekturen|Publish-Subscribe-Architekturen]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Eindeutigkeit|Eindeutigkeit]] der [[Daten|Daten]] erforderlich ist (z. B. in [[Mengen|Mengen]] oder [[Schlüssel-Wert-Speichern|Schlüssel-Wert-Speichern]]). Alternativen wie [[FIFO-Warteschlangen|FIFO-Warteschlangen]] oder [[Transaktionsspeicher|Transaktionsspeicher]] bieten strengere [[Konsistenzmodelle|Konsistenzmodelle]], sind aber weniger flexibel für [[nebenläufige Zugriffe|nebenläufige Zugriffe]].
- **Beispiel / Code:** ```python
# Beispiel: Linda-Tupelraum mit Multimengen-Eigenschaft
blog._out(("bob", "distsys", "Nachricht 1"))  # Tupel 1
blog._out(("bob", "distsys", "Nachricht 1"))  # Tupel 2 (identisch, aber separat gespeichert)

# `in(t)` entfernt EIN passendes Tupel (beliebiges Duplikat)
tupel = blog._in(("bob", "distsys", str))  # Blockiert bis ein Tupel verfügbar ist
```
