---
id: a01478fc-2c75-4c76-9d79-85329f5f6c04
title: "Backlog_Refinement"
date: 2026-05-30
tags:
  - software_engineering
  - agile_methoden
  - scrum
  - anforderungsmanagement
  - user_stories
  - projektplanung
  - software_prozessmodelle
  - draft
source: "Klausur_Referenz"
---

# [[Backlog_Refinement]]

- **Kernkonzept:** Backlog_Refinement (auch als Backlog_Grooming bezeichnet) ist ein wiederkehrender Prozess im [[Scrum]]-Framework, bei dem das [[Product_Backlog]] kontinuierlich überprüft, detailliert, priorisiert und angepasst wird. Ziel ist es, die Einträge (z. B. [[User_Stories]], [[Epics]] oder [[Tasks]]) so vorzubereiten, dass sie für die Aufnahme in einen [[Sprint_Backlog]] geeignet sind. Dabei werden Unklarheiten beseitigt, Abhängigkeiten identifiziert und Schätzungen (z. B. mittels [[Story_Points]]) verfeinert.
- **Nutzen & Zweck:** Backlog_Refinement dient mehreren zentralen Zwecken:
1. **Qualitätssicherung**: Durch frühzeitige Klärung von Anforderungen und Risiken wird die Planungssicherheit erhöht und Nacharbeit im [[Sprint]] reduziert.
2. **Priorisierung**: Das Team und der [[Product_Owner]] einigen sich auf die Reihenfolge der Umsetzung, basierend auf Geschäftswert und Machbarkeit.
3. **Transparenz**: Alle Beteiligten erhalten ein gemeinsames Verständnis der anstehenden Arbeit, was die Zusammenarbeit im [[Scrum_Team]] verbessert.
4. **Flexibilität**: Neue Erkenntnisse oder Änderungen können zeitnah in das Backlog integriert werden, ohne den aktuellen Sprint zu stören.
5. **Effizienz**: Durch die Vorarbeit im Refinement werden [[Sprint_Planning]]-Meetings verkürzt und fokussierter.
- **Abgrenzung & Grenzen:** Backlog_Refinement ist **kein** Ersatz für:
- **[[Sprint_Planning]]**: Hier wird der konkrete Sprint-Backlog erstellt, während Refinement die Vorbereitung dafür leistet.
- **[[Retrospektive]]**: Diese dient der Prozessverbesserung, nicht der inhaltlichen Klärung von Backlog-Einträgen.
- **Anforderungsanalyse im Vorprojekt**: Refinement ist ein **kontinuierlicher** Prozess während der gesamten Projektlaufzeit, nicht nur in der [[Phase_I_Vorprojekt]].

**Typische Stolpersteine**:
- **Zu frühe Detaillierung**: Backlog-Einträge sollten erst kurz vor der Umsetzung im Sprint vollständig spezifiziert werden, um Flexibilität zu erhalten.
- **Fehlende Beteiligung**: Ohne Einbindung des gesamten Scrum-Teams (inkl. [[Development_Team]]) entstehen Wissenslücken oder unrealistische Schätzungen.
- **Überladung**: Zu viele Einträge im Backlog führen zu Unübersichtlichkeit; hier hilft eine klare [[Definition_of_Ready]].
- **Technische Schulden ignorieren**: Refinement sollte auch nicht-funktionale Anforderungen (z. B. Performance, Sicherheit) berücksichtigen.
- **Beispiel / Code:** ```mermaid
classDiagram
    class ProductBacklog {
        +List~BacklogItem~ items
        +priorisieren()
        +verfeinern()
    }
    class BacklogItem {
        <<abstract>>
        +String titel
        +String beschreibung
        +int storyPoints
        +Status status
        +List~Akzeptanzkriterien~ kriterien
    }
    class UserStory {
        +String als
        +String möchteIch
        +String damit
    }
    class Epic {
        +List~UserStory~ untergeschichten
    }
    class Task {
        +String aufgabe
        +int schätzungStunden
    }
    ProductBacklog "1" *-- "0..*" BacklogItem
    BacklogItem <|-- UserStory
    BacklogItem <|-- Epic
    BacklogItem "1" *-- "0..*" Task
    BacklogItem --> Status : hat

    enum Status {
        NEU
        VERFEINERT
        BEREIT
        IN_ARBEIT
        FERTIG
    }
```

**Beispiel für eine verfeinerte User Story (INVEST-Kriterien erfüllt):**
```java
// Vor dem Refinement (unpräzise):
UserStory story1 = new UserStory(
    "Als Nutzer möchte ich meine Daten exportieren.",
    "Damit ich sie extern sichern kann."
);

// Nach dem Refinement (detailliert):
UserStory story1Refined = new UserStory(
    "Als registrierter Nutzer",
    "möchte ich meine persönlichen Daten (Profil, Einstellungen, Uploads) als ZIP-Datei exportieren",
    "damit ich sie lokal sichern oder an einen anderen Dienst übertragen kann."
);
story1Refined.setStoryPoints(5);
story1Refined.addAkzeptanzkriterium("Export enthält alle Datenfelder gemäß Datenbank-Schema.");
story1Refined.addAkzeptanzkriterium("Export ist innerhalb von 30 Sekunden abgeschlossen (für ≤100 MB Daten).");
story1Refined.addAkzeptanzkriterium("Nutzer erhält eine E-Mail mit Download-Link (Gültigkeit: 7 Tage).");
story1Refined.setStatus(Status.BEREIT);
```
