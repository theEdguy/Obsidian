---
id: 58419c30-168e-41c1-a805-239945dc4f59
title: "CAP-Theorem"
date: 2026-06-01
tags:
  - verteilte_systeme
  - theorie
  - konsistenz
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[CAP-Theorem]]

- **Kernkonzept:** Ein Theorem, das besagt, dass ein [[verteiltes_System]] nur zwei der drei Eigenschaften [[Konsistenz]], [[Verfügbarkeit]] und [[Partitionstoleranz]] gleichzeitig garantieren kann.
- **Nutzen & Zweck:** Hilft bei der Auswahl des richtigen [[Konsistenzmodell|Konsistenzmodells]] und der Architektur für [[verteiltes_System|verteilte Systeme]].
- **Abgrenzung & Grenzen:** Kein direktes Design-Prinzip, sondern eine theoretische Einschränkung. Praktische Systeme müssen Kompromisse eingehen.
- **Beispiel / Code:** Ein [[verteiltes_System]] mit hoher Verfügbarkeit und Partitionstoleranz (z. B. Cassandra) opfert starke [[Konsistenz]].
