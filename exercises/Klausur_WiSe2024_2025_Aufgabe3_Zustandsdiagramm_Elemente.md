---
id: a75f9880-16a7-4894-b684-1c67ef4c8eb4
title: "Klausur_WiSe2024_2025_Aufgabe3_Zustandsdiagramm_Elemente"
date: 2026-05-30
tags:
  - software_engineering
  - ws_2024_2025
  - klausur_ws_2024_2025
  - zustandsdiagramm
  - uml
  - zustandsmaschine
  - transitionen
  - analyse
  - exercise
  - draft
source: "SWE-WS-2024-2025 - Loesung.pdf"
---

# [[Klausur_WiSe2024_2025_Aufgabe3_Zustandsdiagramm_Elemente]]

- **Aufgabenstellung:** 
  - **i:** Um was handelt es sich bei den Elementen 1 und 2 in der abgebildeten Skizze eines Zustandsdiagramms?
  - **ii:** Wann erfolgt der Übergang bei Element 3, und was bedeutet die Schreibweise `x [y] / z` im Detail?
  - **iii:** Wann erfolgt der Übergang bei Element 4?
- **Lösungsweg / Musterlösung:** 
  - **i:**
  - **1:** Bei Element 1 handelt es sich um den **Start- bzw. initialen Zustand**. Dieser markiert den Punkt, an dem die [[Zustandsmaschine|Zustandsmaschine]] (oder eine Region davon) beginnt.
    - **2:** Bei Element 2 handelt es sich um einen **History-State**. Dieser speichert die zuletzt aktiven [[Unterzustand|Unterzustände]] von S1. Beim erneuten Betreten von S1 wird nicht zwangsläufig der initiale Unterzustand (z. B. S2) aktiviert, sondern der zuletzt aktive Zustand wiederhergestellt.
  - **ii:**
  - **uebergang:** Der Übergang bei Element 3 erfolgt, sobald im Zustand S1 (oder einem seiner [[Unterzustand|Unterzustände]]) das **Ereignis `x`** eintritt.
    - **bedingung:** Zusätzlich muss die **Bedingung `[y]`** (Guard) erfüllt sein, damit der Übergang stattfindet.
    - **aktion:** Beim Übergang in den Zustand S5 wird die **Aktion `/z`** ausgeführt. Die Schreibweise `x [y] / z` bedeutet also: *Ereignis [Bedingung] / Aktion*.
  - **iii:** Der Übergang bei Element 4 (Completion Transition) erfolgt, sobald **alle parallel ausgeführten [[Region|Regionen]]** in S5 ihre **Finalzustände** erreicht haben. Dies kennzeichnet das Ende der [[Zustandsmaschine|Zustandsmaschine]] oder einer orthogonalen Region.
- **Theoretischer Bezug:** 
  - [[Zustandsdiagramm|Zustandsdiagramme]]
  - [[Zustandsmaschine]]
  - [[Unterzustand]]
  - [[History_State]]
  - [[Transition|Transitionen]]
  - [[Guard_Condition|Guard-Bedingungen]]
  - [[Aktion_(UML)|Aktionen]]
  - [[Region_(UML)|Regionen]]
  - [[Finalzustand]]
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von **Startzustand** und **History-State**: Der Startzustand ist immer der initiale Einstiegspunkt, während der History-State den letzten aktiven Zustand speichert.
  - Fehlinterpretation der Schreibweise `x [y] / z`: Die Reihenfolge (Ereignis → Bedingung → Aktion) wird oft vertauscht oder falsch zugeordnet.
  - Unklare Unterscheidung zwischen **Completion Transition** und ereignisgesteuerten Transitionen: Completion Transitions werden automatisch ausgelöst, sobald alle parallelen Regionen ihre Finalzustände erreichen, während andere Transitionen explizite Ereignisse benötigen.
  - Verkennung der **orthogonalen Regionen** in S5: Parallel ablaufende Regionen müssen alle abgeschlossen sein, bevor der Completion-Übergang erfolgt.
