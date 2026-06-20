---
id: 1dc8ad29-407c-5657-b9ab-9f48b3265752
title: "Drei-Schichten-Architektur"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_10
  - draft
source: "Kapitel 10: Von der Analyse zur Systemarchitektur"
---

# [[Drei-Schichten-Architektur]]

- **Kernkonzept:** Klassisches Architekturmuster:
1. Präsentationsschicht (Presentation): Interaktion mit dem Nutzer (UI).
2. Logikschicht (Logic): Kapselt Geschäftsregeln und Anwendungslogik.
3. Datenhaltungsschicht (Persistence): Verwaltet Datenhaltung und Persistenz.
Regel: Aufrufe dürfen nur von oben nach unten erfolgen (Präsentation -> Logik -> Datenhaltung). Die unteren Schichten kennen die oberen nicht direkt.
- **Nutzen & Zweck:** Klassisches Architekturmuster:
1. Präsentationsschicht (Presentation): Interaktion mit dem Nutzer (UI).
2. Logikschicht (Logic): Kapselt Geschäftsregeln und Anwendungslogik.
3. Datenhaltungsschicht (Persistence): Verwaltet Datenhaltung und Persistenz.
Regel: Aufrufe dürfen nur von oben nach unten erfolgen (Präsentation -> Logik -> Datenhaltung). Die unteren Schichten kennen die oberen nicht direkt.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
