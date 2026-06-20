---
id: 31981232-6c81-5cdc-9d93-7054a13bf7e9
title: "Kapitel_8_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - aktivitaetsdiagramm
  - token_tracing
  - fork_join
  - exercise
  - draft
source: "Kapitel 8 Übung"
---

# Kapitel 8 Aufgabe 2

- **Aufgabenstellung:** Gegeben sei ein Aktivitätsdiagramm mit 5 Aktionen (A bis E) und zwei Swimlanes:
Der Kontrollfluss beginnt mit Aktion A in Swimlane 1. Danach teilt sich der Fluss an einer Fork-Node in zwei parallele Pfade: Pfad 1 führt zu Aktion B in Swimlane 1, Pfad 2 führt zu Aktion C in Swimlane 2. Beide Pfade werden an einer Join-Node zusammengeführt, gefolgt von Aktion D in Swimlane 2. Nach D führt eine Decision-Node bei (cond=true) zu Aktion E, ansonsten endet der Fluss. Beschreiben Sie das Token-Tracing.
- **Lösungsweg / Musterlösung:** 1. Der Fluss startet, ein Token wird an Aktion A (Swimlane 1) übergeben. A wird ausgeführt.
2. Der Token verlässt A und erreicht die Fork-Node. Die Fork-Node dupliziert den Token. Jetzt gibt es zwei parallele Token:
   - Token 1 geht zu Aktion B (Swimlane 1).
   - Token 2 geht zu Aktion C (Swimlane 2).
3. B und C werden unabhängig voneinander ausgeführt.
4. Nach Abschluss von B kommt Token 1 an der Join-Node an und wartet dort, bis auch C abgeschlossen ist (Token 2 kommt an).
5. Erst wenn beide Token am Join vorliegen, verschmilzt der Join sie zu einem einzigen Token und gibt ihn an Aktion D (Swimlane 2) weiter.
6. D wird ausgeführt. Danach entscheidet die Decision-Node:
   - Wenn cond=true: Token geht zu E, E wird ausgeführt, danach Endknoten.
   - Wenn cond=false: Der Fluss endet direkt.
- **Theoretischer Bezug:** [[Kapitel_8__Use_Cases_verstehen]]
- **Stolpersteine / Fehlerquellen:** Vergessen, dass Join blockiert, bis *alle* eingehenden Pfade einen Token geliefert haben. Verwechslung von Fork/Join (Parallelität, dicker Balken) mit Decision/Merge (Alternative, Raute).
