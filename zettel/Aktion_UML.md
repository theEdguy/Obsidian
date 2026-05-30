---
id: f9d7b7f7-6813-4cc9-b71c-cec06208fddb
title: "Aktion_UML"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - aktivitätsdiagramm
  - use_case
  - objektorientierte_analyse
  - softwarearchitektur
  - draft
source: "Klausur_Referenz"
---

# [[Aktion_UML]]

- **Kernkonzept:** Eine **Aktion** in [[UML]] (Unified Modeling Language) ist ein grundlegender Baustein in [[Aktivitätsdiagrammen]] und [[Interaktionsdiagrammen]], der eine ausführbare atomare Einheit innerhalb eines Prozesses oder einer Verhaltensbeschreibung darstellt. Sie repräsentiert eine einzelne Operation, Berechnung oder einen Schritt, der während der Ausführung eines Systems stattfindet. Aktionen sind typischerweise nicht weiter zerlegbar und werden als Rechtecke mit abgerundeten Ecken dargestellt, oft mit einem beschreibenden Text (z. B. "Mitglied hinzufügen"). In [[Sequenzdiagrammen]] oder [[Kommunikationsdiagrammen]] können Aktionen als Nachrichten oder Methodenaufrufe zwischen Objekten modelliert werden.
- **Nutzen & Zweck:** Aktionen dienen der präzisen Modellierung von Verhalten in [[UML-Diagrammen]], insbesondere zur:
- **Dokumentation von Workflows**: Sie ermöglichen die Darstellung von Abläufen in [[Aktivitätsdiagrammen]], z. B. für Geschäftsprozesse oder Systemoperationen.
- **Verfeinerung von [[Use_Cases]]**: Aktionen konkretisieren die Schritte innerhalb eines [[Use_Case-Diagramms]], z. B. durch Zuordnung zu [[Systemoperationen]] in [[Interaktionsdiagrammen]].
- **Brücke zwischen Analyse und Design**: Sie helfen, Anforderungen (z. B. aus [[User_Stories]]) in technische Spezifikationen zu überführen, indem sie konkrete Verarbeitungsschritte definieren.
- **Unterstützung der [[Objektorientierten_Analyse_und_Design|OOAD]]**: Aktionen sind essenziell für die Modellierung von [[Zustandsautomaten]] oder die Detaillierung von [[Kollaborationen]] zwischen Objekten.

Durch ihre Atomarität fördern Aktionen die Klarheit und Nachvollziehbarkeit von Modellen, was besonders in agilen Entwicklungsprozessen (z. B. [[Unified_Process]]) oder bei der Erstellung von [[Softwarearchitektur-Dokumentation]] wertvoll ist.
- **Abgrenzung & Grenzen:** **Abgrenzung zu ähnlichen Konzepten:**
- **Aktivität vs. Aktion**: Eine [[Aktivität_UML]] ist eine größere Einheit, die aus mehreren Aktionen bestehen kann und oft Kontrollstrukturen (z. B. Schleifen) enthält. Aktionen sind dagegen atomar.
- **Nachricht vs. Aktion**: In [[Sequenzdiagrammen]] ist eine Nachricht (z. B. ein Methodenaufruf) eine Kommunikation zwischen Objekten, während eine Aktion den ausführbaren Schritt selbst beschreibt.
- **Operation vs. Aktion**: Eine [[Operation]] (z. B. in einer [[Klasse]]) ist eine Signatur, während eine Aktion deren konkrete Ausführung im Kontext eines Diagramms darstellt.

**Typische Stolpersteine:**
- **Zu grobe Granularität**: Aktionen sollten nicht zu komplex sein (z. B. "Datenbank migrieren"), da dies die Lesbarkeit von Diagrammen beeinträchtigt. Besser: Aufteilen in kleinere Aktionen (z. B. "Backup erstellen", "Schema aktualisieren").
- **Fehlende Kontextbindung**: Aktionen ohne klare Zuordnung zu [[Akteuren]] oder [[Systemgrenzen]] können zu Missverständnissen führen. Beispiel: Eine Aktion "Benutzer anlegen" sollte im Kontext eines [[Use_Case-Diagramms]] oder [[Aktivitätsdiagramms]] stehen.
- **Vermischung mit Implementierungsdetails**: Aktionen sollten technologieunabhängig formuliert sein (z. B. "Bestellung bestätigen" statt "HTTP-Request senden").
- **Unklare Verantwortlichkeiten**: In [[Interaktionsdiagrammen]] muss klar sein, welches Objekt eine Aktion ausführt (z. B. durch Zuordnung zu [[Lebenslinien]]).
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt ein [[Aktivitätsdiagramm]] mit Aktionen zur Modellierung des Workflows "Mitglieder verwalten" aus dem gegebenen Kontext. Die Aktionen sind atomar und beschreiben die Schritte innerhalb des Prozesses:', 'uml_mermaid': '```mermaid\nactivityDiagram\n    title Mitglieder verwalten (Aktivitätsdiagramm)\n    start\n    :Mitgliedsdaten eingeben;\n    :Daten validieren;\n    if (Daten gültig?) then\n        :Mitglied in Datenbank speichern;\n        :Bestätigungs-E-Mail generieren;\n        :E-Mail versenden;\n        stop\n    else\n        :Fehlermeldung anzeigen;\n        stop\n    endif\n```', 'erlaeuterung': '1. **Aktionen im Diagramm**:\n   - "Mitgliedsdaten eingeben": Atomare Eingabeaktion (z. B. durch einen [[Akteur]] wie den Vereinsmanager).\n   - "Daten validieren": Überprüfung der Eingaben (z. B. auf Vollständigkeit).\n   - "Mitglied in Datenbank speichern": Persistenzaktion, die eine [[Systemoperation]] auslöst.\n   - "Bestätigungs-E-Mail generieren": Vorbereitung einer Nachricht (z. B. durch ein [[Entwurfsmuster|Template_Method_Pattern]]).\n\n2. **Kontrollfluss**: Die Verzweigung (if-else) zeigt, wie Aktionen in Abhängigkeit von Bedingungen ausgeführt werden.\n\n3. **Bezug zum Kontext**: Die Aktionen konkretisieren den [[Use_Case]] "Mitglieder verwalten" und könnten in einem [[Sequenzdiagramm]] weiter detailliert werden (z. B. durch Nachrichten zwischen Objekten wie `Vereinsmanager -> Mitglied: hinzufügen()`).'}
