---
id: 62b84b6f-ca54-4e85-af42-4d651857b51b
title: "Soft Link (Symbolischer Link)"
date: 2026-06-02
tags:
  - verteilte_systeme
  - benennung
  - namensraum
  - verteilte-systeme
  - dateisysteme
  - referenzierung
  - namensauflösung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Soft Link (Symbolischer Link)]]

- **Kernkonzept:** Ein [[Soft Link|Soft Link]] (auch symbolischer Link genannt) ist ein [[Verweis|Verweis]] in einem [[Namensraum|Namensraum]], der den [[Name|Namen]] eines anderen [[Knoten|Knotens]] enthält. Die [[Namensauflösung]] folgt zunächst dem [[Soft Link|Soft Link]] und setzt dann mit dem referenzierten [[Name|Namen]] fort.
- **Nutzen & Zweck:** Ein [[Soft Link|Soft Link]] ermöglicht flexible [[Verknüpfung|Verknüpfungen]] zwischen [[Entität|Entitäten]] in einem [[Namensraum]], ohne die [[Struktur]] des [[Benennungsgraph|Benennungsgraphen]] direkt zu verändern. Er löst das [[Problem]] der [[Redundanz]] und [[Mehrfachreferenzierung]], indem er indirekte [[Zugriffspfade]] schafft, die dynamisch aufgelöst werden.
- **Abgrenzung & Grenzen:** Ein [[Soft Link|Soft Link]] sollte nicht genutzt werden, wenn direkte [[Verweise]] (z. B. [[Hard Link|Hard Links]]) erforderlich sind, da er bei [[Löschung]] des Ziels ins Leere führt (sog. [[Dangling Link|Dangling Link]]). Im Gegensatz zu [[Hard Link|Hard Links]] verweist er nicht auf die [[Entität]] selbst, sondern auf deren [[Name]], was zusätzliche [[Namensauflösung]]sschritte erfordert. Für [[Performance]]-kritische Anwendungen sind direkte [[Verweise]] oft effizienter.
- **Beispiel / Code:** Im Dateisystem unter Unix/Linux:
```bash
# Erstellt einen symbolischen Link 'keys_link' auf '/home/steen/keys'
ln -s /home/steen/keys keys_link

# Auflösungsprozess:
# 1. Zugriff auf 'keys_link' → liest Inhalt '/home/steen/keys'
# 2. Setzt Namensauflösung mit '/home/steen/keys' fort
```

Im [[Benennungsgraph|Benennungsgraph]] (vgl. Folie 23):
- Knoten `n5` enthält den [[Name|Namen]] `/home/steen/keys` (Soft Link).
- Die Auflösung von `n5` führt zur Weiterleitung an Knoten `n6`.
