---
id: 2f40cc0b-3f04-4b46-b9f4-b03bde74e7c4
title: "High-Level Beschreibung"
date: 2026-06-23
tags:
  - software_engineering
  - übersicht
  - beschreibung
  - draft
source: "software_engineering_kapitel_07"
---

# [[High-Level Beschreibung]]

- **Kernkonzept:** Eine High-Level-Beschreibung ist eine kompakte, überblicksartige Darstellung eines Use Cases, die die zentralen Abläufe und Interaktionen zwischen Akteuren und System in wenigen Sätzen zusammenfasst. Sie dient als erste grobe Skizze des Anwendungsfalls ohne detaillierte Schritt-für-Schritt-Anleitung.
- **Nutzen & Zweck:** Dieses Konzept existiert, um frühzeitig ein gemeinsames Problemverständnis zwischen Stakeholdern, Entwicklern und Analysten zu schaffen. Es löst das Problem, dass komplexe Anforderungen ohne strukturierte Übersicht schwer kommunizierbar und priorisierbar sind. Durch die kompakte Form können Use Cases schnell bewertet, verglichen und in die Gesamtarchitektur eingeordnet werden, bevor aufwendige Detailanalysen erfolgen.
- **Abgrenzung & Grenzen:** Eine High-Level-Beschreibung sollte nicht genutzt werden, wenn detaillierte Prozessschritte, Ausnahmefälle oder technische Implementierungsdetails entscheidend sind. Sie unterscheidet sich von erweiterten Use-Case-Beschreibungen durch ihre Kürze und Abstraktion – letztere sind für die spätere Entwicklungsphase gedacht, wenn präzise Spezifikationen benötigt werden. Zudem eignet sie sich nicht für die Dokumentation von Einzelschritten oder technischen Schnittstellen.
- **Beispiel / Code:** ```java
// Beispiel einer High-Level-Beschreibung als Kommentar im Use-Case-Diagramm
/*
Use Case: Mitglieder verwalten
- Akteure: Vereinsmanager, Mail Client
- System: MyClub
- Beschreibung: Der Vereinsmanager kann Mitgliederdaten (Anlegen, Bearbeiten, Löschen) pflegen.
  Bei Abteilungswechseln werden betroffene Akteure automatisch per E-Mail informiert.
  Passive Mitglieder ohne Abteilungszuordnung werden gesondert gekennzeichnet.
*/
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b5a
- **Vorgänger / Parent:** [[Use_Case_Beschreibung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case_Beschreibung]]
