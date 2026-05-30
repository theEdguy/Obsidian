---
id: b9d6f2fe-6cda-4ba1-8722-82ba28db41c2
title: "Anforderung_Software_Engineering"
date: 2026-05-30
tags:
  - software_engineering
  - anforderungsanalyse
  - spezifikation
  - qualitaetssicherung
  - agile_entwicklung
  - use_case
  - nicht_funktionale_anforderungen
  - ieee_830
  - draft
source: "Klausur_Referenz"
---

# [[Anforderung_Software_Engineering]]

- **Kernkonzept:** Eine **Anforderung** im [[Software_Engineering]] ist eine präzise formulierte Bedingung oder Fähigkeit, die ein System erfüllen muss, um ein definiertes Problem zu lösen oder ein Ziel zu erreichen. Anforderungen beschreiben *was* ein System leisten soll (funktionale Anforderungen) oder *wie gut* es dies tun soll (nicht-funktionale Anforderungen), ohne vorzugeben, *wie* die Umsetzung erfolgt. Sie dienen als Brücke zwischen Stakeholdern (z. B. Kunden, Entwicklern) und dem [[System_Design]] und sind Grundlage für [[Anforderungsanalyse]], [[Spezifikation]] und [[Validierung]].
- **Nutzen & Zweck:** Anforderungen erfüllen folgende zentrale Zwecke:
1. **Kommunikation**: Sie schaffen eine gemeinsame Sprache zwischen Stakeholdern und Entwicklern, um Missverständnisse zu vermeiden.
2. **Planung & Schätzung**: Sie bilden die Basis für Projektplanung, Aufwandsschätzung (z. B. [[Use_Case_Points]]) und Priorisierung.
3. **Qualitätssicherung**: Durch [[Anforderungs_Tracing]] und [[Testfall_Generierung]] ermöglichen sie die Überprüfung der Systemkonformität.
4. **Flexibilität**: Gut formulierte Anforderungen (z. B. nach [[INVEST_Kriterien]]) erlauben Anpassungen an wechselnde Kundenwünsche, ohne den Kern der Lösung zu verändern (Prinzip der [[Trennung_von_Belangen]]).
5. **Risikominimierung**: Frühzeitige Identifikation von Konflikten oder Unklarheiten reduziert spätere Nacharbeiten (vgl. [[V-Modell]]).
- **Abgrenzung & Grenzen:** 1. **Funktional vs. Nicht-funktional**: 
   - *Funktionale Anforderungen* sind objektiv (z. B. "Das System muss Bestellungen speichern") und entweder erfüllt oder nicht.
   - *Nicht-funktionale Anforderungen* (z. B. [[Performance]], [[Sicherheit]], [[Benutzerfreundlichkeit]]) sind subjektiv und erfordern Metriken (z. B. "95% der Anfragen müssen in <2s beantwortet werden").
2. **Stolpersteine**:
   - *Unklare Formulierungen*: Anforderungen wie "Das System soll benutzerfreundlich sein" sind nicht messbar. Besser: "Die durchschnittliche Einarbeitungszeit für neue Nutzer beträgt <30 Minuten."
   - *Überlappung mit Design*: Anforderungen beschreiben *was*, nicht *wie* (z. B. "Datenbankabfragen" sind Design, "Daten müssen persistent gespeichert werden" ist eine Anforderung).
   - *Änderungsmanagement*: Anforderungen sind dynamisch; starre [[Spezifikationsdokumente]] ohne [[Change_Management]] führen zu Scope Creep.
3. **Grenzen**:
   - Anforderungen ersetzen keine [[User_Stories]] oder [[Use_Cases]], sondern ergänzen diese.
   - Sie sind kein Ersatz für [[Prototyping]] oder iterative [[Feedbackschleifen]] (vgl. [[Agile_Entwicklung]]).
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer strukturierten Anforderungsspezifikation (textuell, angelehnt an [[IEEE_830]]) mit funktionalen und nicht-funktionalen Anteilen:', 'beispiel': {'funktional': {'id': 'FA-12', 'beschreibung': 'Das System muss registrierten Nutzern ermöglichen, Artikel in einen Warenkorb zu legen und diesen zu bearbeiten (Hinzufügen, Löschen, Mengenänderung).', 'priorität': 'Hoch', 'akzeptanzkriterien': ['Ein Artikel kann nur einmal im Warenkorb liegen (Menge wird erhöht).', 'Die Gesamtanzahl der Artikel im Warenkorb wird in Echtzeit aktualisiert.']}, 'nicht_funktional': {'id': 'NFA-5', 'beschreibung': 'Die Ladezeit der Warenkorb-Seite darf bei 100 gleichzeitigen Nutzern 1,5 Sekunden nicht überschreiten.', 'metrik': '95. Perzentil der Antwortzeit (gemessen mit [[JMeter]])', 'priorität': 'Mittel'}}, 'uml_diagramm': {'typ': 'Mermaid', 'code': 'classDiagram\n    class Kunde {\n        +String name\n        +Warenkorb warenkorb\n        +artikelHinzufuegen(artikel: Artikel)\n        +artikelEntfernen(artikel: Artikel)\n    }\n    class Warenkorb {\n        -List~Artikel~ artikelListe\n        +gesamtpreisBerechnen() float\n        +artikelHinzufuegen(artikel: Artikel)\n        +artikelEntfernen(artikel: Artikel)\n    }\n    class Artikel {\n        +String id\n        +String name\n        +float preis\n        +int menge\n    }\n    Kunde "1" *-- "1" Warenkorb : enthält\n    Warenkorb "1" *-- "*" Artikel : enthält\n    note for Warenkorb "Anforderung FA-12: Warenkorb muss\n    Bearbeitungsfunktionen bereitstellen."'}}
