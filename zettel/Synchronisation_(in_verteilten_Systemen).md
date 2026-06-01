---
id: b0f97121-6d0c-4673-8094-03e1093d9eea
title: "Synchronisation (in verteilten Systemen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - koordination
  - konsistenz
  - grundlagen
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Synchronisation (in verteilten Systemen)]]

- **Kernkonzept:** [[Synchronisation]] in [[verteilten Systemen]] bezeichnet Mechanismen, um die [[Aktion|Aktionen]] autonomer [[Knoten]] zeitlich oder logisch aufeinander abzustimmen, trotz fehlender globaler Uhr.
- **Nutzen & Zweck:** Ermöglicht die [[Koordination]] von [[Knoten]], um [[Konsistenz]] und korrekte [[Ablauf|Abläufe]] in [[Systemen]] ohne zentrale Steuerung zu gewährleisten. Löst das Problem der [[Race-Condition|Race-Conditions]] und inkonsistenter [[Zustand|Zustände]].
- **Abgrenzung & Grenzen:** Führt zu Overhead und Latenz, da [[Knoten]] aufeinander warten müssen. Nicht geeignet für Anwendungen mit strikten Echtzeitanforderungen. Unterscheidet sich von [[Synchronisation]] in [[zentralisierten Systemen]] durch dezentrale Protokolle.
- **Beispiel / Code:** Das [[Lamport-Uhr]]-Protokoll verwendet logische [[Zeitstempel]], um die [[Reihenfolge]] von [[Ereignis|Ereignissen]] in [[verteilten Systemen]] zu bestimmen.
