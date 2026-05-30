---
id: 8326de40-ef1f-4696-8931-a6b85881acab
title: "Problemraum"
date: 2026-05-30
tags:
  - software_engineering
  - systemanalyse
  - anforderungsengineering
  - use_case
  - domänenmodellierung
  - softwareentwurf
  - draft
source: "Klausur_Referenz"
---

# [[Problemraum]]

- **Kernkonzept:** Der **Problemraum** bezeichnet im Kontext des [[Software_Engineering]] und der [[Systemanalyse]] die abstrakte Domäne, in der ein zu lösendes Problem existiert. Er umfasst alle relevanten Anforderungen, Randbedingungen, Akteure, Ziele und Konflikte, die für die Problembeschreibung und spätere Lösungserarbeitung (im [[Lösungsraum]]) essenziell sind. Der Problemraum wird durch eine strukturierte Analyse (z. B. mittels [[Use_Case_Diagramm]] oder [[Anforderungsdokumentation]]) erfasst und dient als Grundlage für die Modellierung im [[Lösungsraum]].
- **Nutzen & Zweck:** Der Problemraum erfüllt folgende zentrale Zwecke:
1. **Klärung der Problemdomäne**: Er zwingt Entwickler:innen, das Problem vor der Implementierung präzise zu verstehen, um Fehlentwicklungen (z. B. durch falsche Annahmen) zu vermeiden.
2. **Kommunikationsgrundlage**: Er schafft eine gemeinsame Sprache zwischen Stakeholdern (z. B. Kund:innen, Entwickler:innen) und reduziert Missverständnisse.
3. **Trennung von Analyse und Design**: Durch die explizite Abgrenzung zum [[Lösungsraum]] wird verhindert, dass Lösungsdetails zu früh in die Problembeschreibung einfließen (vgl. [[Separation_of_Concerns]]).
4. **Risikominimierung**: Eine gründliche Problemraumanalyse identifiziert frühzeitig Konflikte (z. B. widersprüchliche Anforderungen) oder nicht-funktionale Randbedingungen (z. B. Performance-Anforderungen).
- **Abgrenzung & Grenzen:** 1. **Keine Lösungsskizze**: Der Problemraum beschreibt *was* das Problem ist, nicht *wie* es gelöst wird. Lösungsansätze gehören in den [[Lösungsraum]].
2. **Dynamische Natur**: Der Problemraum ist nicht statisch – neue Anforderungen oder Erkenntnisse können ihn erweitern oder verändern (vgl. [[Agile_Entwicklung]]).
3. **Subjektivität**: Die Definition des Problemraums hängt stark von der Perspektive der Stakeholder ab. Beispiel: Eine Kund:in sieht ein Usability-Problem, während Entwickler:innen ein Performance-Problem priorisieren.
4. **Stolpersteine**:
   - **Überanalyse**: Zu detaillierte Problemraumbeschreibungen können zu Lähmung führen (vgl. [[Analysis_Paralysis]]).
   - **Vernachlässigung**: Wird der Problemraum zu oberflächlich behandelt, entstehen Lösungen, die das eigentliche Problem nicht adressieren (vgl. [[XY_Problem]]).
   - **Vermischung mit Lösungsraum**: Typischer Fehler ist die frühzeitige Festlegung auf Technologien (z. B. "Wir brauchen eine [[Microservices]]-Architektur") statt der Fokussierung auf das Problem.
- **Beispiel / Code:** ```mermaid
classDiagram
    class Problemraum {
        +String beschreibung
        +List~Akteur~ akteure
        +List~Anforderung~ funktionaleAnforderungen
        +List~Anforderung~ nichtFunktionaleAnforderungen
        +List~Randbedingung~ randbedingungen
        +analysiere() Problemmodell
    }
    
    class Akteur {
        +String name
        +String rolle
    }
    
    class Anforderung {
        +String id
        +String text
        +Priorität priorität
    }
    
    class Randbedingung {
        +String beschreibung
        +Typ typ
    }
    
    Problemraum "1" *-- "0..*" Akteur : umfasst
    Problemraum "1" *-- "1..*" Anforderung : enthält
    Problemraum "1" *-- "0..*" Randbedingung : berücksichtigt
```

**Textuelles Beispiel (Use-Case-Extrakt für ein Bibliothekssystem):**
- **Akteure**: Bibliothekar:in, Nutzer:in, Systemadministrator:in
- **Funktionale Anforderungen**:
  - FR-1: Nutzer:innen müssen Bücher ausleihen können.
  - FR-2: Bibliothekar:innen müssen Ausleihfristen verwalten.
- **Nicht-funktionale Anforderungen**:
  - NFR-1: Das System muss 99,9% Verfügbarkeit bieten.
  - NFR-2: Die Suche nach Büchern darf max. 2 Sekunden dauern.
- **Randbedingungen**:
  - RB-1: Das System muss mit der bestehenden Datenbank kompatibel sein.
  - RB-2: Die Implementierung muss innerhalb von 6 Monaten abgeschlossen sein.
