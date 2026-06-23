---
id: e2379c8b-1180-485e-827f-ac9689b990b8
title: "Use Case Beschreibung"
date: 2026-06-23
tags:
  - software_engineering
  - beschreibung
  - dokumentation
  - analyse
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Use Case Beschreibung]]

- **Kernkonzept:** Eine [[Use_Case_Beschreibung|Use-Case-Beschreibung]] ist eine strukturierte Darstellung eines [[Anwendungsfall|Anwendungsfalls]], die den Ablauf einer Interaktion zwischen [[Akteur|Akteuren]] und einem [[System]] aus Nutzersicht dokumentiert. Sie umfasst zentrale Elemente wie Name, [[Akteur|Akteure]], [[Systemgrenze]], Priorität, Anforderungen und eine detaillierte oder hochlevelige Ablaufbeschreibung, um die [[funktionale_Anforderung|funktionalen Anforderungen]] eines [[System|Systems]] zu spezifizieren und die [[Problemdomäne]] zu verstehen.
- **Nutzen & Zweck:** Use-Case-Beschreibungen dienen dazu, [[funktionale_Anforderung|funktionale Anforderungen]] an ein [[System]] verständlich und nachvollziehbar zu erfassen, zu priorisieren und zu kommunizieren. Sie bilden die Grundlage für die weitere [[Anforderungsanalyse]], [[Systemarchitektur]], Implementierung und [[Testplanung]], indem sie sicherstellen, dass alle [[Stakeholder]] ein gemeinsames Verständnis der [[Systemfunktion|Systemfunktionen]] und -ziele entwickeln. Zudem helfen sie, komplexe [[Prozess|Prozesse]] in handhabbare Einheiten zu zerlegen, [[Risiko|Risiken]] frühzeitig zu identifizieren und die Kommunikation zwischen [[Stakeholder|Stakeholdern]] zu verbessern. Durch die systematische Erfassung von Abläufen, [[Akteur|Akteuren]] und [[Systemreaktion|Systemreaktionen]] wird die Problemdomäne klarer definiert und die Grundlage für das [[Systemdesign]] gelegt.
- **Abgrenzung & Grenzen:** Use-Case-Beschreibungen sollten nicht für die Dokumentation einzelner technischer Schritte, isolierter Aktionen oder [[nicht-funktionale_Anforderung|nicht-funktionaler Anforderungen]] (z. B. [[Performance]], [[Sicherheit]]) verwendet werden, da sie zusammenhängende Abläufe aus Nutzersicht abbilden. Sie eignen sich nicht für die Darstellung zeitlicher Abfolgen mehrerer [[Use_Case|Use Cases]] oder detaillierter Implementierungsdetails. Alternativen wie [[User_Story|User Stories]] (agile Entwicklung) oder funktionale Spezifikationen können sinnvoller sein, wenn es um sehr feingranulare oder rein technische [[Anforderung|Anforderungen]] geht. Zudem ersetzen Use-Case-Beschreibungen keine detaillierten [[Datenmodell|Datenmodelle]], [[Algorithmus|Algorithmen]] oder technische [[Spezifikation|Spezifikationen]], sondern dienen primär der [[Anforderungsanalyse]]. Im Vergleich zu [[User_Story|User Stories]] sind sie formaler aufgebaut und fokussieren sich auf detaillierte Abläufe statt auf kurze, zielorientierte Aussagen.
- **Beispiel / Code:** ```java
// Beispiel einer strukturierten Use-Case-Beschreibung (textuelle Dokumentation, kein ausführbarer Code)

Use Case: Mitglieder verwalten
Systemgrenze: MyClub-System
Primärer Akteur: Vereinsmanager
Sekundäre Akteure: Mail Client
Priorität: 1 (hoch)
Vorbedingungen: MyClub ist installiert, der Vereinsmanager ist authentisiert.
Anforderungen: F1.1, F1.2, F2.1
Ziel: Mitgliederdaten im System anlegen, bearbeiten oder löschen.

Hauptszenario:
1. Der Vereinsmanager wählt zwischen Neuanlage, Bearbeitung oder Löschung eines Mitglieds.
2. Das System zeigt ein Formular zur Eingabe oder Änderung der Mitgliedsdaten an.
3. Der Vereinsmanager gibt die Daten ein (Name, Adresse, Abteilung, etc.).
4. Das System validiert die Eingaben.
5. Das System speichert die Änderungen und bestätigt die erfolgreiche Durchführung.
6. Bei Änderungen (z. B. Adresse, Abteilung) werden betroffene Akteure per Mail informiert.
7. Mitglieder ohne Abteilungszugehörigkeit werden als "passiv" markiert.

Alternativszenario:
4a. Die Eingaben sind ungültig.
4a1. Das System zeigt eine Fehlermeldung an.
4a2. Der Vereinsmanager korrigiert die Eingaben und fährt mit Schritt 4 fort.

Nachbedingungen: Die Mitgliederdaten sind im System aktualisiert.
Offene Punkte: Benachrichtigungsregeln für Mitglieder bei Änderungen klären.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Use-Case-basierte_Analyse]]
- **Folgezettel / Unterzettel:**
  - [[Ablaufbeschreibung]]
  - [[Vorbedingung]]
  - [[Nachbedingung]]
  - [[Ausnahme]]
- **Querverweise:**
  - [[Textuelle_Analyse]]
  - [[Anforderungsdokumentation]]
