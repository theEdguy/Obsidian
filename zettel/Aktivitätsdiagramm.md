---
id: afa2c1ad-4372-4975-80ea-e9361418bc45
title: "Aktivitätsdiagramm"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - modellierung
  - prozessdesign
  - systemanalyse
  - use_case
  - draft
source: "Klausur_Referenz"
---

# [[Aktivitätsdiagramm]]

- **Kernkonzept:** Ein [[Aktivitätsdiagramm]] ist eine grafische Darstellung von Arbeitsabläufen (Aktivitäten) und Kontrollflüssen in einem System, die sowohl sequentielle als auch parallele Prozesse modelliert. Es gehört zur [[UML]] und visualisiert den dynamischen Aspekt eines Systems durch Knoten (Aktionen, Entscheidungen, Start-/Endpunkte) und Kanten (Kontrollflüsse). Aktivitätsdiagramme eignen sich besonders zur Abbildung von [[Use_Cases]], Geschäftsprozessen oder Algorithmen, da sie komplexe Logik (z. B. Schleifen, Verzweigungen, Synchronisation) intuitiv abbilden.
- **Nutzen & Zweck:** Aktivitätsdiagramme dienen primär der:
- **Dokumentation von Prozessen**: Sie machen Abläufe für Stakeholder (Entwickler, Analysten, Kunden) verständlich, z. B. zur Spezifikation von [[Anforderungen]].
- **Analyse und Optimierung**: Durch die Visualisierung lassen sich Engpässe, Redundanzen oder Parallelisierungspotenziale identifizieren.
- **Implementierungsvorbereitung**: Sie unterstützen die Ableitung von [[Zustandsdiagrammen]], [[Sequenzdiagrammen]] oder Code-Strukturen (z. B. für [[Workflow_Engines]]).
- **Kommunikation**: Sie überbrücken die Lücke zwischen fachlichen Anforderungen und technischer Umsetzung, ähnlich wie [[BPMN]]-Diagramme, sind aber stärker auf Software-Systeme fokussiert.
- **Abgrenzung & Grenzen:** - **Kein Ersatz für [[Sequenzdiagramme]]**: Aktivitätsdiagramme zeigen *was* passiert, aber nicht *wer* (Akteure/Objekte) es tut. Für Interaktionen zwischen Komponenten sind Sequenzdiagramme besser geeignet.
- **Keine Datenflüsse**: Im Gegensatz zu [[Datenflussdiagrammen]] modellieren sie keine Datenflüsse, sondern Kontrollflüsse. Daten können jedoch als Objekte in den Fluss eingebettet werden.
- **Komplexitätsgrenzen**: Bei extrem verschachtelten Prozessen werden Diagramme unübersichtlich. Hier helfen Unteraktivitäten ("Raffungen") oder die Aufteilung in Teil-Diagramme.
- **Keine Zeitachse**: Die Dauer von Aktivitäten wird nicht dargestellt (im Gegensatz zu [[Gantt-Diagrammen]]).
- **Stolpersteine**: Häufige Fehler sind unklare Start-/Endpunkte, fehlende Synchronisation bei parallelen Pfaden oder die Vermischung von Kontroll- und Datenflüssen.
- **Beispiel / Code:** {'beschreibung': "Aktivitätsdiagramm für den Use Case 'Bestellung aufgeben' (textuelle UML-Notation mit Mermaid-Syntax):", 'mermaid': '```mermaid\nactivityDiagram\n  title Aktivitätsdiagramm: Bestellung aufgeben\n  start\n  :Kunde wählt Produkte;\n  :System prüft Lagerbestand;\n  if (Produkte verfügbar?) then (ja)\n    :System berechnet Gesamtpreis;\n    :Kunde gibt Zahlungsdaten ein;\n    :System validiert Zahlung;\n    if (Zahlung erfolgreich?) then (ja)\n      :System bestätigt Bestellung;\n      :System aktualisiert Lager;\n      :System sendet Bestätigungsmail;\n      stop\n    else (nein)\n      :System bricht Bestellung ab;\n      stop\n    endif\n  else (nein)\n    :System informiert über Nichtverfügbarkeit;\n    stop\n  endif\n```', 'hinweis': 'Die Aktionen können in der Praxis den Operationen `op1` (Lagerprüfung), `op2` (Preisberechnung) und `op3` (Zahlungsvalidierung) zugeordnet werden, wie in der Aufgabenstellung gefordert.'}
