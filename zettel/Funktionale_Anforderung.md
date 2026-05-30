---
id: 33adb76b-ecf5-484e-969c-28a1e894b1fe
title: "Funktionale_Anforderung"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - qualitaetssicherung
  - software_quality
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Funktionale_Anforderung]]

- **Kernkonzept:** Eine [[Anforderung]], die beschreibt, **was** ein [[Softwaresystem]] leisten soll, indem sie konkrete [[Funktionalität|Funktionalitäten]] oder [[Verhalten|Verhaltensweisen]] des Systems definiert, die für den [[Endbenutzer]] oder andere [[Systemkomponente|Systemkomponenten]] sichtbar und überprüfbar sind. Ergänzend definiert die [[Nichtfunktionale_Anforderung|nicht-funktionale Anforderung]] [[Qualitätsmerkmal|Qualitätsmerkmale]] wie [[Performance]], [[Sicherheit]], [[Skalierbarkeit]] oder [[Benutzerfreundlichkeit]], die beschreiben, **wie gut** das System diese [[Funktionalität|Funktionalitäten]] erbringen soll.
- **Nutzen & Zweck:** Funktionale [[Anforderung|Anforderungen]] lösen das Problem unklarer [[Zielvorgabe|Zielvorgaben]] durch präzise Definition der erwarteten [[Funktionalität|Funktionalitäten]], um die [[Geschäftsprozess|Geschäftsprozesse]] der [[Stakeholder]] zu unterstützen. Sie definieren *was* das [[Softwaresystem]] tun soll (z. B. [[Daten_validieren|Daten validieren]], [[Transaktion_durchführen|Transaktionen durchführen]]) und bilden die Grundlage für [[Testfall|Testfälle]] sowie [[Akzeptanzkriterium|Akzeptanzkriterien]]. [[Nichtfunktionale_Anforderung|Nicht-funktionale Anforderungen]] ergänzen dies, indem sie messbare [[Metrik|Metriken]] für die [[Qualitätsbewertung]] bereitstellen und sicherstellen, dass das System nicht nur funktioniert, sondern auch [[zuverlässig]], [[sicher]] und [[wartbar]] ist. Ohne sie können [[Systemausfall|Systemausfälle]], [[Sicherheitslücke|Sicherheitslücken]] oder [[Performance-Problem|Performance-Probleme]] entstehen, die die [[Nutzerakzeptanz]] gefährden.
- **Abgrenzung & Grenzen:** Funktionale und [[Nichtfunktionale_Anforderung|nicht-funktionale Anforderungen]] sind komplementär, ersetzen sich jedoch nicht gegenseitig. Funktionale [[Anforderung|Anforderungen]] beschreiben konkrete [[Aktion|Aktionen]] des [[Softwaresystem|Systems]], während [[Nichtfunktionale_Anforderung|nicht-funktionale Anforderungen]] [[Qualitätsmerkmal|Qualitätsmerkmale]] wie [[Performance]], [[Sicherheit]] oder [[Skalierbarkeit]] adressieren. Zu viele [[Anforderung|Anforderungen]] können die Priorisierung erschweren. [[Nichtfunktionale_Anforderung|Nicht-funktionale Anforderungen]] sind ohne definierte [[Metrik|Metriken]] schwer überprüfbar und erfordern oft Kompromisse zwischen [[Qualitätsmerkmal|Qualitätsmerkmalen]] (z. B. [[Leistung]] vs. [[Sicherheit]]). Zudem sollten funktionale [[Anforderung|Anforderungen]] nicht mit [[Implementierungsdetail|Implementierungsdetails]] vermischt werden, um die [[Flexibilität]] der [[Lösung]] zu wahren. Im Gegensatz zu funktionalen [[Anforderung|Anforderungen]] sind nicht-funktionale [[Anforderung|Anforderungen]] oft [[querschnittlich]] (z. B. [[Sicherheit]] betrifft mehrere [[Komponente|Komponenten]]) und sollten bereits im [[Architekturentwurf]] berücksichtigt werden, nicht erst in der [[Implementierung]].
- **Beispiel / Code:** ```plaintext
// Beispiel für eine funktionale Anforderung
FR-002: Mitgliederliste exportieren
Beschreibung: Das System muss eine Liste aller Mitglieder als CSV-Datei exportieren.
Priorität: Mittel
Akzeptanzkriterium: Die exportierte Datei enthält Name, Adresse und Mitgliedsnummer.

// Ergänzendes Beispiel für eine funktionale Anforderung
F1.5: Der [[Mail-Versand]] muss protokolliert werden, inkl. Zeitstempel und Empfänger.

// Beispiel für eine nicht-funktionale Anforderung
NFR-001: Antwortzeit
Beschreibung: Das System muss 95% aller Anfragen innerhalb von 2 Sekunden beantworten.
Metrik: Durchschnittliche Antwortzeit < 2s (gemessen über 1 Stunde).
Priorität: Hoch

// Beispiel für eine nicht-funktionale Sicherheitsanforderung
A1.7: Der Versand von [[Mitgliederliste|Mitgliederlisten]] muss mit [[AES-256]] verschlüsselt erfolgen.
```
