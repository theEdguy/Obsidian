---
id: 2fcb967b-d5cf-4947-aee0-d61ea7303fe9
title: "Metrik"
date: 2026-05-30
tags:
  - software_engineering
  - qualitaetssicherung
  - messung
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Metrik]]

- **Kernkonzept:** Eine messbare Größe zur Bewertung von [[Qualitätsmerkmal|Qualitätsmerkmalen]] in [[Softwaresystem|Systemen]]. Dient der Objektivierung von [[Nichtfunktionale_Anforderung|nicht-funktionalen Anforderungen]].
- **Nutzen & Zweck:** Löst das Problem der subjektiven Bewertung von [[Qualität]] durch quantifizierbare [[Zielvorgabe|Zielvorgaben]]. Ermöglicht die Überprüfung von [[Nichtfunktionale_Anforderung|nicht-funktionalen Anforderungen]] und kontinuierliche Verbesserung.
- **Abgrenzung & Grenzen:** Kein Ersatz für qualitative Bewertungen (z. B. [[Benutzerfreundlichkeit]]). Bei falscher Wahl der [[Metrik|Metriken]] können Fehlanreize entstehen (z. B. Optimierung der [[Leistung]] auf Kosten der [[Wartbarkeit]]).
- **Beispiel / Code:** ```plaintext
// Beispiel-Metriken für ein Softwaresystem
- Leistung: Antwortzeit (95. Perzentil) < 500ms
- Zuverlässigkeit: Mittlere Zeit bis zum Ausfall (MTBF) > 30 Tage
- Wartbarkeit: Durchschnittliche Zeit zur Fehlerbehebung < 4 Stunden
```
