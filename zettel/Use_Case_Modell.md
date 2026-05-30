---
id: 821e0d63-4047-4f90-804b-b5684c4a9e48
title: "Use_Case_Modell"
date: 2026-05-30
tags:
  - software_engineering
  - analyse
  - modellierung
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Use_Case_Modell]]

- **Kernkonzept:** Ein [[Modell]] zur Beschreibung der [[Funktionalität]] eines [[Softwaresystem|Systems]] aus Sicht der [[Akteur|Akteure]]. Zeigt, wie [[Akteur|Akteure]] mit dem System interagieren, um Ziele zu erreichen.
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Systemgrenze]] und [[Nutzerinteraktion]] durch strukturierte Darstellung der [[Anwendungsfall|Anwendungsfälle]]. Dient als Grundlage für [[Testfall|Testfälle]] und [[Designentscheidung|Designentscheidungen]].
- **Abgrenzung & Grenzen:** Kein Ersatz für detaillierte [[Prozessmodellierung]] oder [[Datenmodellierung]]. Bei zu vielen [[Anwendungsfall|Anwendungsfällen]] kann die Übersichtlichkeit leiden. Nicht geeignet für Systeme ohne klare [[Akteur|Akteure]].
- **Beispiel / Code:** ```plaintext
// Beispiel für einen Use Case
Use Case: Mitglied anlegen
Akteur: Vereinsadministrator
Beschreibung: Der Administrator erfasst ein neues Mitglied im System.
Hauptszenario:
1. Administrator wählt "Mitglied anlegen".
2. System zeigt Eingabemaske.
3. Administrator gibt Daten ein.
4. System validiert Daten.
5. System speichert Mitglied.
```
