---
id: 86c873b1-55d5-4cd6-bd41-c4605ba6fc89
title: "Hierarchische Domänen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - namensauflösung
  - skalierbarkeit
  - hierarchie
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchische Domänen]]

- **Kernkonzept:** Hierarchische Domänen strukturieren ein [[verteiltes System]] in verschachtelte [[Domäne|Domänen]], die durch [[Verzeichnisknoten]] repräsentiert werden. Dies ermöglicht eine skalierbare [[Namensauflösung]] durch schrittweise Suche entlang der Hierarchie.
- **Nutzen & Zweck:** Das Konzept löst das [[Skalierbarkeitsproblem]] bei der [[Auflösung]] linearer [[Name|Namen]] in großen [[Netzwerk|Netzwerken]], indem es die Suche auf relevante [[Domäne|Domänen]] beschränkt und so die Last verteilt. Es vermeidet die Ineffizienz von [[Broadcasting]] oder zentralen [[Namensdienst|Namensdiensten]].
- **Abgrenzung & Grenzen:** Nicht geeignet für hochdynamische Systeme mit häufigen [[Entität|Entitäts]]-Umzügen, da die Hierarchie statisch ist. Alternativen wie [[verteilte Hash-Tabelle|verteilte Hash-Tabellen]] (z. B. [[Chord]]) skalieren besser für flache [[Name|Namen]], erfordern aber komplexere [[Routing]]-Mechanismen. [[Heimatbasierte Ansätze]] sind einfacher, aber weniger flexibel bei geografischer Verteilung.
- **Beispiel / Code:** Beispiel für eine hierarchische Domänenstruktur (HLS):
```
Top-Level-Domäne: T (Verzeichnisknoten: dir(T))
├── Subdomäne: S (dir(S))
│   ├── Blattdomäne: A (dir(A))
│   └── Blattdomäne: B (dir(B))
└── Subdomäne: U (dir(U))
```
Suche nach Entität `E` in Domäne `A`:
1. Anfrage an `dir(A)` → nicht gefunden.
2. Weiterleitung an `dir(S)` → nicht gefunden.
3. Weiterleitung an `dir(T)` → Rückgabe der Adresse von `E` in `A`.
