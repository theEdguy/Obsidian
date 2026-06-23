---
id: 09e9d089-1239-47f7-b51c-61727768d61d
title: "Erweiterte Use Cases"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - detaillierung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Erweiterte Use Cases]]

- **Kernkonzept:** Erweiterte Use Cases sind detaillierte Beschreibungen von Abläufen in einem Softwaresystem, die über die grobe Übersicht von High-Level-Use-Cases hinausgehen und die Interaktionen zwischen Akteuren und System unter Berücksichtigung von Bedingungen, Alternativszenarien und technischen Details präzise darstellen.
- **Nutzen & Zweck:** Erweiterte Use Cases dienen dazu, komplexe Anforderungen und Abläufe im Softwareentwicklungsprozess präzise zu dokumentieren und zu kommunizieren. Sie lösen das Problem, dass High-Level-Use-Cases oft zu oberflächlich sind, um als Grundlage für Design, Implementierung und Test zu dienen. Durch die detaillierte Ausarbeitung werden Missverständnisse vermieden, Risiken frühzeitig erkannt und die Grundlage für eine stabile Architektur sowie spätere Testfälle geschaffen.
- **Abgrenzung & Grenzen:** Erweiterte Use Cases sollten nicht genutzt werden, wenn die Anforderungen noch unklar oder stark veränderlich sind, da der Aufwand für die detaillierte Ausarbeitung dann ineffizient ist. Sie unterscheiden sich von High-Level-Use-Cases durch ihren höheren Detaillierungsgrad und sind keine Alternative zu User Stories im agilen Kontext, da sie weniger flexibel und stärker prozessorientiert sind. Zudem eignen sie sich nicht für triviale oder stark standardisierte Abläufe, bei denen eine einfache Beschreibung ausreicht.
- **Beispiel / Code:** ```java
// Beispiel: Erweiterter Use Case "Mitglied anlegen" in strukturierter Form
UseCase MitgliedAnlegen {
    Name: "Mitglied anlegen"
    Akteure: Vereinsmanager, MailClient
    Systemgrenze: MyClub
    Priorität: 1 (hoch)
    Vorbedingung: Vereinsmanager ist authentisiert, System ist betriebsbereit.
    
    Hauptszenario:
    1. Vereinsmanager wählt "Neues Mitglied anlegen" aus.
    2. System zeigt Eingabemaske für Mitgliedsdaten an.
    3. Vereinsmanager gibt Daten ein (Name, Adresse, Abteilung).
    4. System validiert die Eingaben.
    5. System speichert das Mitglied und generiert eine Mitgliedsnummer.
    6. System sendet Bestätigungsmail an das Mitglied (via MailClient).
    
    Alternativszenarien:
    4a. Eingaben sind ungültig:
        4a1. System zeigt Fehlermeldung an.
        4a2. Weiter mit Schritt 3.
    
    6a. Mailversand schlägt fehl:
        6a1. System protokolliert Fehler und zeigt Hinweis an.
        6a2. Vereinsmanager kann manuell eine Mail versenden.
    
    Nachbedingung: Mitglied ist im System angelegt und aktiv.
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a2
- **Vorgänger / Parent:** [[Use_Case_Analyse]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungsanalyse]]
