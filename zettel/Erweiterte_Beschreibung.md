---
id: 3175b975-d7c4-4fa5-b7ba-b1f8bf50f085
title: "Erweiterte Beschreibung"
date: 2026-06-23
tags:
  - software_engineering
  - detaillierung
  - beschreibung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Erweiterte Beschreibung]]

- **Kernkonzept:** Eine erweiterte Beschreibung im Kontext von Use Cases ist eine detaillierte Darstellung der Abläufe, Interaktionen und Szenarien zwischen Akteuren und dem System, die über eine grobe Übersicht hinausgeht und alle relevanten Schritte, Bedingungen sowie Ausnahmen umfasst.
- **Nutzen & Zweck:** Dieses Konzept existiert, um komplexe oder kritische Anwendungsfälle präzise zu dokumentieren und Missverständnisse in der Kommunikation zwischen Stakeholdern, Entwicklern und Testern zu vermeiden. Es löst das Problem unklarer oder unvollständiger Anforderungen, indem es alle notwendigen Details für die Implementierung, das Testen und die Wartung bereitstellt. Zudem dient es als Grundlage für die Ableitung von Testfällen und die Identifikation von Systemgrenzen.
- **Abgrenzung & Grenzen:** Eine erweiterte Beschreibung sollte nicht für einfache oder triviale Use Cases verwendet werden, da sie unnötigen Aufwand verursacht. Sie unterscheidet sich von High-Level-Use-Cases, die lediglich eine grobe Übersicht bieten und primär der ersten Problemverständigung dienen. Zudem ist sie nicht geeignet, um technische Implementierungsdetails oder Algorithmen zu beschreiben – hierfür sind andere Artefakte wie Sequenzdiagramme oder Pseudocode besser geeignet. Bei stark standardisierten oder repetitiven Abläufen kann eine erweiterte Beschreibung redundant sein.
- **Beispiel / Code:** ```java
// Beispiel: Erweiterte Beschreibung als strukturierter Text (kein Code, aber formalisiert)
Use Case: "Mitglieder verwalten" (erweitert)
Akteure: Vereinsmanager, Mail Client
Vorbedingung: System ist betriebsbereit, Vereinsmanager ist authentisiert.
Hauptszenario:
1. Vereinsmanager wählt Option "Mitglieder verwalten" aus dem Hauptmenü.
2. System zeigt Liste aller Mitglieder an.
3. Vereinsmanager wählt eine der folgenden Optionen:
   a) Neues Mitglied anlegen (→ Schritt 4)
   b) Bestehendes Mitglied bearbeiten (→ Schritt 5)
   c) Mitglied löschen (→ Schritt 6)
4. System öffnet Eingabemaske für neue Mitglieder.
   - Vereinsmanager gibt Daten ein (Name, Adresse, Abteilung).
   - System validiert Eingaben und speichert das Mitglied.
   - System sendet Bestätigungsmail an das Mitglied.
   - Use Case endet.
5. System lädt Daten des ausgewählten Mitglieds.
   - Vereinsmanager ändert relevante Felder (z. B. Adresse).
   - System validiert Änderungen und speichert sie.
   - Bei Abteilungswechsel: System sendet Benachrichtigung an Abteilungsleiter und Mitglied.
   - Use Case endet.
6. System fragt nach Bestätigung für Löschung.
   - Bei Bestätigung: System löscht Mitglied und informiert Abteilungsleiter.
   - Use Case endet.
Alternativszenarien:
- 3a: Keine Mitglieder vorhanden → System zeigt Hinweis an.
- 4/5: Validierung schlägt fehl → System zeigt Fehlermeldung und fordert Korrektur.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b5b
- **Vorgänger / Parent:** [[Use_Case_Beschreibung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Beschreibung]]
