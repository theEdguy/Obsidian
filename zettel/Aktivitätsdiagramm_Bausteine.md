---
id: 50931a32-66f4-44d5-bdcd-297d29059e61
title: "Aktivitätsdiagramm Bausteine"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_08"
---

# [[Aktivitätsdiagramm Bausteine]]

- **Kernkonzept:** Aktivitätsdiagramme sind UML-Diagramme, die Abläufe, Workflows oder Algorithmen durch zusammenhängende Aktionen und deren Übergänge modellieren. Sie visualisieren den Kontroll- und Datenfluss zwischen Aktivitäten und Akteuren in einem System oder Prozess.
- **Nutzen & Zweck:** Aktivitätsdiagramme dienen dazu, komplexe Abläufe verständlich darzustellen und zu analysieren. Sie lösen das Problem der unklaren oder mehrdeutigen Beschreibung von Prozessen, indem sie Interaktionen, Entscheidungen, Parallelität und Verantwortlichkeiten grafisch strukturieren. Dadurch unterstützen sie die Kommunikation zwischen Stakeholdern, die Identifikation von Optimierungspotenzialen und die Grundlage für die Implementierung von Software oder Geschäftsprozessen.
- **Abgrenzung & Grenzen:** Aktivitätsdiagramme sollten nicht genutzt werden, wenn der Fokus auf der detaillierten Beschreibung von Zuständen einzelner Objekte liegt – hier sind Zustandsdiagramme besser geeignet. Sie eignen sich weniger für die Darstellung statischer Strukturen (z. B. Klassenbeziehungen), wofür Klassendiagramme vorzuziehen sind. Zudem sind sie ungeeignet für die Modellierung von Echtzeit-Systemen mit strengen Zeitvorgaben, da sie keine zeitlichen Constraints explizit abbilden. Im Vergleich zu Sequenzdiagrammen fehlt ihnen die präzise Darstellung der zeitlichen Abfolge von Nachrichten zwischen Objekten.
- **Beispiel / Code:** ```java
// Beispiel: Aktivitätsdiagramm als Pseudocode für einen Mitgliedschaftsprozess
start
  if (Mitglied beitreten?) then
    [ja] -> Mitgliedsdaten erfassen -> Beitrag berechnen -> Mitglied speichern -> Willkommensmail senden -> end
    [nein] -> Abbruch -> end
  endif
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a
- **Vorgänger / Parent:** [[Aktivitätsdiagramm]]
- **Folgezettel / Unterzettel:**
  - [[Aktion]]
  - [[Entscheidung]]
  - [[Split]]
  - [[Join]]
  - [[Objektknoten]]
  - [[Parameter]]
  - [[Swimlane]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
