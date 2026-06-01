---
id: 45d36ae8-91cc-497e-b11f-39736ba951dc
title: "Verteilte_Shared_Memory"
date: 2026-06-01
tags:
  - verteilte_systeme
  - hochleistungsrechnen
  - speicherverwaltung
  - paralleles_rechnen
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Verteilte_Shared_Memory]]

- **Kernkonzept:** Ein Modell, das den [[Hauptspeicher]] mehrerer [[Maschine|Maschinen]] als einen einzigen virtuellen Adressraum darstellt, um parallele Berechnungen zu ermöglichen.
- **Nutzen & Zweck:** Vereinfacht die Programmierung von parallelen Anwendungen, indem es den Zugriff auf entfernte Speicherbereiche wie lokalen Speicher behandelt.
- **Abgrenzung & Grenzen:** Hohe Latenz und begrenzte Skalierbarkeit im Vergleich zu [[Multi-Prozessor]]-Systemen. Wurde weitgehend durch andere Ansätze ersetzt.
- **Beispiel / Code:** Ein Prozess auf [[Maschine]] A greift auf eine Speicherseite von [[Maschine]] B zu, als wäre sie lokal verfügbar.
