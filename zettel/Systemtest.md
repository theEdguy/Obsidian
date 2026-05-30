---
id: 78134bf1-3a89-4c9c-8404-4765100ee9a2
title: "Systemtest"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - system_testing
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Systemtest]]

- **Kernkonzept:** Ein [[Test]] auf der höchsten [[Testebene]], der das [[Softwaresystem]] als Ganzes überprüft. Fokussiert auf die Erfüllung der [[Anforderung|Anforderungen]] und die Validierung der [[Nichtfunktionale_Anforderung|nicht-funktionalen Anforderungen]].
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Systemqualität]] durch ganzheitliche Überprüfung der [[Funktionalität]] und [[Qualitätsmerkmal|Qualitätsmerkmale]]. Grundlage für die [[Abnahme]] durch [[Stakeholder|Stakeholder]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Modultest|Modultests]] oder [[Integrationstest|Integrationstests]]. Bei unklaren [[Anforderung|Anforderungen]] können [[Testfall|Testfälle]] schwer definierbar sein. Erfordert oft komplexe [[Testumgebung|Testumgebungen]].
- **Beispiel / Code:** ```plaintext
// Beispiel für einen Systemtest
Testfall: TC-001 - Mitgliederverwaltung
Beschreibung: Test der gesamten Mitgliederverwaltung.
Schritte:
1. Mitglied anlegen.
2. Adresse ändern.
3. Beitrag berechnen.
4. Mitgliederliste exportieren.
Erwartetes Ergebnis: Alle Schritte funktionieren ohne Fehler.
```
