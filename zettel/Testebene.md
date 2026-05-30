---
id: 7cf5acee-37d8-4906-b7c5-5eee26d9ba73
title: "Testebene"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - qualitaetssicherung
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Testebene]]

- **Kernkonzept:** Eine hierarchische Stufe im [[Testprozess]], die sich auf einen bestimmten [[Abstraktionsgrad]] des [[Softwaresystem|Systems]] konzentriert. Typische Ebenen sind [[Modultest]], [[Integrationstest]] und [[Systemtest]].
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Testabdeckung]] durch systematische Überprüfung auf verschiedenen [[Abstraktionsgrad|Abstraktionsgraden]]. Ermöglicht frühzeitige Fehlererkennung und gezielte [[Fehlerlokalisierung]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Akzeptanztest|Akzeptanztests]], die die [[Nutzerperspektive]] einnehmen. Erfordert klare [[Schnittstelle|Schnittstellen]] zwischen den [[Testebene|Testebenen]]. Bei unklaren [[Testziel|Testzielen]] kann die Effizienz leiden.
- **Beispiel / Code:** ```plaintext
// Beispiel für Testebenen in einem Projekt
1. Modultest: Test der Klasse Mitglied (White-Box-Test)
2. Integrationstest: Test der Interaktion zwischen Mitglied und Beitragsmodul
3. Systemtest: Test der Mitgliederverwaltung als Gesamtsystem
4. Akzeptanztest: Test durch den Verein "SV Hoch und Weit"
```
