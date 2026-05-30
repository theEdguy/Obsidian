---
id: 424bde3e-9b91-4321-9e00-bae090387d8e
title: "Akzeptanztest"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - abnahme
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Akzeptanztest]]

- **Kernkonzept:** Ein [[Test]], der die [[Abnahme]] des [[Softwaresystem|Systems]] durch den [[Kunde|Kunden]] oder [[Endbenutzer]] vorbereitet. Überprüft die Erfüllung der [[Anforderung|Anforderungen]] aus [[Nutzerperspektive]].
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Kundenzufriedenheit]] durch Validierung der [[Funktionalität]] aus Sicht der [[Endbenutzer]]. Grundlage für die offizielle [[Abnahme]] und Auslieferung.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Systemtest|Systemtests]] oder [[Nichtfunktionale_Anforderung|nicht-funktionale Tests]]. Bei unklaren [[Anforderung|Anforderungen]] können [[Testfall|Testfälle]] schwer definierbar sein. Erfordert oft [[Benutzerbeteiligung]].
- **Beispiel / Code:** ```plaintext
// Beispiel für einen Akzeptanztest
User Story: Als Vereinsadministrator möchte ich Mitgliederdaten ändern können.
Akzeptanzkriterien:
- Die Änderung wird im System gespeichert.
- Eine Bestätigungsmail wird an das Mitglied gesendet.
- Die Änderung ist sofort in der Mitgliederliste sichtbar.
```
