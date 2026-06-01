---
id: 2cc84475-f917-4e69-82f2-468eac5f2484
title: "Fehlender globaler Zeitbegriff"
date: 2026-06-01
tags:
  - verteilte_systeme
  - grundlagen
  - synchronisation
  - koordination
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Fehlender globaler Zeitbegriff]]

- **Kernkonzept:** In [[verteilten Systemen]] existiert keine globale Uhr, da [[Knoten]] autonome [[Rechenelement|Rechenelemente]] mit eigenen [[Zeitmessung|Zeitmessungen]] sind. Dies führt zu Herausforderungen bei der [[Synchronisation]] und [[Koordination]].
- **Nutzen & Zweck:** Erzwingt den Einsatz logischer [[Uhr|Uhren]] oder [[Synchronisationsprotokoll|Synchronisationsprotokolle]], um [[Konsistenz]] und [[Koordination]] zu ermöglichen. Löst das Problem der Abhängigkeit von physikalischen Uhren in dezentralen Umgebungen.
- **Abgrenzung & Grenzen:** Führt zu komplexen Protokollen wie [[Lamport-Uhr|Lamport-Uhren]] oder [[Vektor-Uhr|Vektor-Uhren]], die zusätzlichen Overhead verursachen. Nicht relevant für [[zentralisierte Systeme]], die eine gemeinsame Uhr nutzen können.
- **Beispiel / Code:** Mit [[Lamport-Uhr|Lamport-Uhren]] wird eine logische [[Reihenfolge]] von [[Ereignis|Ereignissen]] in [[verteilten Systemen]] hergestellt, ohne auf eine globale Uhr angewiesen zu sein.
