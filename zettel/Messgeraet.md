---
id: 7421c30b-7372-47b4-b8f6-17300829921e
title: "Messgeraet"
date: 2026-05-31
tags:
  - software_engineering
  - metriken
  - agile_entwicklung
  - uml
  - monitoring
  - qualitaetssicherung
  - draft
source: "Klausur_Referenz"
---

# [[Messgeraet]]

- **Kernkonzept:** Ein [[Messgeraet]] ist ein abstraktes oder konkretes Konstrukt im [[Software_Engineering]], das dazu dient, quantifizierbare Metriken oder Zustände eines Systems, Prozesses oder einer Komponente zu erfassen, zu verarbeiten und darzustellen. Es fungiert als Schnittstelle zwischen dem zu messenden Objekt (z. B. [[Meilenstein]], [[Fortschrittsindikator]] oder [[Systemlast]]) und den Akteuren (z. B. Entwickler, [[Product_Owner]]), die diese Daten interpretieren. Messgeräte können sowohl technische Implementierungen (z. B. Logging-Frameworks, Monitoring-Tools) als auch konzeptionelle Modelle (z. B. [[Use_Case_Diagramm]] zur Fortschrittsvisualisierung) umfassen.
- **Nutzen & Zweck:** Messgeräte dienen primär der Transparenz und Steuerung in Softwareprojekten oder -systemen. Sie ermöglichen:
1. **Fortschrittskontrolle**: Erkennung von Verzögerungen oder Erreichen von [[Meilenstein]]en (z. B. durch [[Burndown_Chart]] oder [[Gantt_Diagramm]]).
2. **Qualitätssicherung**: Erfassung von Metriken wie Code-Coverage, Fehlerraten oder Performance (z. B. mittels [[Profiling_Tool]]).
3. **Entscheidungsunterstützung**: Bereitstellung von Daten für [[Retrospektive]] oder Priorisierung (z. B. [[Velocity_Tracking]] in [[Scrum]]).
4. **Automatisierung**: Integration in [[CI/CD_Pipeline]] zur dynamischen Anpassung (z. B. Skalierung von [[Worker_Thread]]-Pools basierend auf Lastmetriken).

Beispiele:
- **Technisch**: Prometheus für Systemmetriken, SonarQube für Code-Qualität.
- **Konzeptionell**: [[Use_Case_Diagramm]] zur Darstellung von Nutzerinteraktionen mit einem Haushaltsbuch (z. B. 'Transaktionen filtern').
- **Abgrenzung & Grenzen:** 1. **Abgrenzung zu reinen Datensammlern**: Ein Messgerät geht über reine Datenspeicherung (z. B. [[Datenbank]]) hinaus, indem es Daten *interpretierbar* aufbereitet (z. B. durch Aggregation oder Visualisierung).
2. **Kontextabhängigkeit**: Die Wahl des Messgeräts hängt vom Ziel ab – ein [[Burndown_Chart]] misst Fortschritt, ein [[Load_Test]] Performance. Mischformen (z. B. kombinierte Metriken) können zu Fehlinterpretationen führen.
3. **Stolpersteine**:
   - **Übermessung**: Zu viele Metriken führen zu 'Analysis Paralysis' (z. B. tägliche Erfassung von 50 KPIs).
   - **Fehlende Kalibrierung**: Messgeräte müssen an Projektziele angepasst werden (z. B. [[Story_Point]]-Skala in [[Agile_Entwicklung]]).
   - **Technische Limitationen**: Echtzeit-Messgeräte (z. B. [[APM_Tool]]) können Systemressourcen belasten.
4. **Kein Ersatz für Kommunikation**: Messgeräte liefern Daten, ersetzen aber nicht [[Stakeholder]]-Feedback (z. B. im [[Sprint_Review]]).
- **Beispiel / Code:** {'beschreibung': "Skizze eines [[Use_Case_Diagramms]] für das Haushaltsbuch 'myHaushalt' (basierend auf Frau Müllers Kickoff-Meeting). Das Diagramm visualisiert Messgeräte als Akteure oder Systemkomponenten:", 'uml_mermaid': '```mermaid\nuseCaseDiagram\n    actor "Frau Müller (Product Owner)" as PO\n    actor "Entwickler" as Dev\n    actor "Bank-API" as Bank\n    \n    rectangle myHaushalt {\n        usecase "Transaktionen importieren" as UC1\n        usecase "Kategorien zuweisen" as UC2\n        usecase "Ausgaben analysieren" as UC3\n        usecase "Fortschritt messen" as UC4\n        usecase "Meilenstein prüfen" as UC5\n    }\n    \n    PO --> UC1\n    PO --> UC2\n    PO --> UC3\n    Dev --> UC4\n    Dev --> UC5\n    Bank --> UC1\n    \n    note right of UC4\n        Messgerät: [[Burndown_Chart]]\n        Metrik: "Anzahl offener User Stories"\n    end note\n    \n    note right of UC5\n        Messgerät: [[Meilenstein_Tracker]]\n        Metrik: "Erfüllte Akzeptanzkriterien"\n    end note\n```', 'java_beispiel': {'beschreibung': 'Einfaches Messgerät zur Erfassung von Code-Coverage (JUnit + JaCoCo):', 'code': '// Beispiel: JUnit-Test mit Coverage-Messung\nimport org.junit.jupiter.api.Test;\nimport static org.junit.jupiter.api.Assertions.*;\n\npublic class HaushaltsbuchTest {\n    @Test\n    public void testTransaktionImport() {\n        Haushaltsbuch hb = new Haushaltsbuch();\n        hb.importiereTransaktion("2023-10-01;Einkauf;-50.00");\n        assertEquals(1, hb.getTransaktionen().size());\n        // Messgerät: JaCoCo erfasst, ob diese Zeile ausgeführt wurde\n    }\n}\n// Konfiguration in build.gradle:\n// plugins { id \'jacoco\' }\n// jacoco { toolVersion = "0.8.11" }'}}
