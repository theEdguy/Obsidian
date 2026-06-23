---
id: 24950599-0fa5-47bc-9a82-e5accd74b7d2
title: "History-Zustand"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - systemmodellierung
  - zustand
  - gedächtnis
  - draft
source: "software_engineering_kapitel_12"
---

# [[History-Zustand]]

- **Kernkonzept:** [[History-Zustand|History-Zustände]] sind ein spezielles [[Konzept]] in [[UML]]-[[Zustandsdiagramm|Zustandsdiagrammen]], das sich den zuletzt aktiven [[Unterzustand]] eines [[Zusammengesetzter_Zustand|zusammengesetzten Zustands]] merkt. Beim erneuten Betreten des übergeordneten [[Zustand|Zustands]] wird automatisch der gespeicherte [[Unterzustand]] wiederhergestellt, statt in den initialen [[Zustand]] zurückzukehren.
- **Nutzen & Zweck:** [[History-Zustand|History-Zustände]] lösen das [[Problem]], dass [[System|Systeme]] nach Unterbrechungen oder temporären [[Zustandsübergang|Zustandswechseln]] nahtlos an der vorherigen Stelle fortfahren müssen. Sie vermeiden manuelle Wiederherstellungslogik und erhöhen die [[Kohäsion]] sowie [[Übersichtlichkeit]] von [[Zustandsdiagramm|Zustandsdiagrammen]], indem sie den letzten [[Kontext]] implizit speichern. Dies ist besonders nützlich in [[Workflow|Workflows]], die unterbrechbar sind, oder in [[System|Systemen]] mit mehreren [[Bearbeitungsschritt|Bearbeitungsschritten]], die später fortgesetzt werden sollen. Zudem reduzieren sie die [[Komplexität]] bei der Modellierung von [[Event-gesteuertes_System|Event-gesteuerten Systemen]], da sie [[Zustandsübergang|Zustandsübergänge]] deklarativ abbilden.
- **Abgrenzung & Grenzen:** [[History-Zustand|History-Zustände]] sind nicht geeignet für [[System|Systeme]], bei denen der initiale [[Zustand]] nach jedem Betreten zwingend erforderlich ist, da sie diesen überschreiben. Sie eignen sich zudem nicht für einfache [[Zustandsautomat|Zustandsautomaten]] ohne [[Unterzustand|Unterzustände]] oder wenn die [[Zustandsgeschichte]] irrelevant ist. In solchen Fällen sind Alternativen wie explizite Speicherung des letzten [[Zustand|Zustands]] in [[Variable|Variablen]] oder [[Stack-basierte_Zustandsverwaltung|Stack-basierte Ansätze]] vorzuziehen, da sie mehr [[Kontrolle]] bieten – allerdings auf Kosten zusätzlicher [[Implementierungslogik]] und geringerer [[Deklarativität]].
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> Bearbeitung
    state Bearbeitung {
        [*] --> Schritt1
        Schritt1 --> Schritt2: nächster Schritt
        Schritt2 --> Schritt3: nächster Schritt
        Schritt3 --> Schritt2: zurück
        --
        H*: History
    }
    Bearbeitung --> Unterbrechung: Pause
    Unterbrechung --> Bearbeitung: Fortsetzen
    Bearbeitung --> [*]: Fertig

    note right of Bearbeitung
        Beim Verlassen und Wiederbetreten von "Bearbeitung"
        wird der letzte aktive Unterzustand (z. B. "Schritt2")
        über den History-Zustand (H*) wiederhergestellt.
    end note
```

```java
// Pseudocode zur Veranschaulichung der Logik hinter History-Zuständen
class BearbeitungsWorkflow {
    Zustand aktuellerZustand = Zustand.SCHRITT1;
    Zustand letzterUnterzustand = null;
    
    void unterbrechen() {
        letzterUnterzustand = aktuellerZustand;
    }
    
    void fortsetzen() {
        if (letzterUnterzustand != null) {
            aktuellerZustand = letzterUnterzustand;
        } else {
            aktuellerZustand = Zustand.SCHRITT1; // Initialer Zustand
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3a3
- **Vorgänger / Parent:** [[Zustandsdiagramme]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Protokoll-Automaten]]
  - [[Zustandsdiagramme]]
