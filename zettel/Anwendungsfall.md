---
id: 29047152-1ccb-4ba4-8395-ad3988fbd72c
title: "Anwendungsfall"
date: 2026-05-30
tags:
  - software_engineering
  - anforderungsanalyse
  - modellierung
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Anwendungsfall]]

- **Kernkonzept:** Ein [[Anwendungsfall]] beschreibt eine funktionale [[Anforderung]] aus Sicht eines [[Akteur|Akteurs]], der mit dem System interagiert, um ein bestimmtes Ziel zu erreichen. Er definiert die Interaktion zwischen [[Akteur|Akteuren]] und System.
- **Nutzen & Zweck:** Er hilft, die [[Systemgrenze|Systemgrenzen]] zu klären und die [[Anforderung|Anforderungen]] aus Benutzersicht zu dokumentieren. [[Anwendungsfall|Anwendungsfälle]] bilden die Grundlage für [[Use-Case-Diagramm|Use-Case-Diagramme]] und die [[Priorisierung]] von Entwicklungsaufgaben.
- **Abgrenzung & Grenzen:** Kein Ersatz für nicht-funktionale [[Anforderung|Anforderungen]] (z. B. Performance, Sicherheit). Im Gegensatz zu [[User_Story|User Stories]] sind [[Anwendungsfall|Anwendungsfälle]] detaillierter und formaler dokumentiert.
- **Beispiel / Code:** ```text
Anwendungsfall: Bestellung aufgeben
Akteur: Kunde
Vorbedingung: Kunde ist eingeloggt
Hauptszenario:
1. Kunde wählt Produkte aus.
2. System zeigt Warenkorb an.
3. Kunde bestätigt Bestellung.
4. System leitet zur Zahlung weiter.
Nachbedingung: Bestellung ist im System erfasst.
```
