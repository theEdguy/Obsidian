---
id: f89d73e3-077c-4642-9098-6b7c47b132ae
title: "Architekturentscheidung"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Architekturentscheidung]]

- **Kernkonzept:** [[Architekturentscheidung|Architekturentscheidungen]] sind grundlegende Festlegungen in der [[Systemarchitektur]], die die Struktur, [[Technologie|Technologien]] und [[Designprinzip|Designprinzipien]] eines Systems prägen. Sie umfassen z. B. die Wahl der [[Datenhaltung]], [[Ablauflogik]] oder [[Parallelität]].
- **Nutzen & Zweck:** Sie schaffen eine stabile Grundlage für die [[Implementierung]] und beeinflussen die [[Skalierbarkeit]], [[Performance]] und [[Wartbarkeit]] des Systems. [[Architekturentscheidung|Architekturentscheidungen]] sind schwer rückgängig zu machen und erfordern sorgfältige Abwägung.
- **Abgrenzung & Grenzen:** Kein Ersatz für detaillierte [[Design]]-Entscheidungen oder [[Implementierung]]. Sie beschreiben nur die grobe Richtung, nicht die konkrete Umsetzung. Im Gegensatz zu [[Anforderung|Anforderungen]] sind sie technisch geprägt.
- **Beispiel / Code:** ```text
Architekturentscheidung: Datenhaltung
- Strategie: Relationale Datenbank (PostgreSQL)
- Begründung: ACID-Konformität für Finanztransaktionen
- Alternativen: NoSQL (MongoDB), In-Memory (Redis)
```
