---
id: 6af30635-0ffc-4770-a39e-5c421d86ca62
title: "Loesungsraum"
date: 2026-05-30
tags:
  - software_engineering
  - softwareentwurf
  - entwurfsmuster
  - grasp
  - architekturprinzipien
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Loesungsraum]]

- **Kernkonzept:** Der **Lösungsraum** bezeichnet im Kontext des [[Softwareentwurfs]] die Menge aller möglichen Design- und Implementierungsalternativen, die zur Erfüllung der Anforderungen eines Systems zur Verfügung stehen. Er umfasst strukturelle und verhaltensbezogene Entscheidungen, wie die Zuweisung von [[Verantwortlichkeiten]] zu [[Klassen]] und [[Komponenten]], die Wahl von [[Entwurfsmustern]] oder die Festlegung von [[Schnittstellen]]. Der Lösungsraum ist eng mit Prinzipien wie [[Lose_Kopplung]] und [[Hohe_Kohäsion]] verknüpft, die als Leitplanken für die Exploration und Eingrenzung der Optionen dienen.
- **Nutzen & Zweck:** Der Lösungsraum dient als gedankliches Framework, um systematisch Design-Entscheidungen zu evaluieren und zu optimieren. Sein Nutzen liegt in:
- **Strukturierter Entscheidungsfindung**: Durch die explizite Betrachtung aller Alternativen werden suboptimale Lösungen (z. B. [[God_Object]]) vermieden.
- **Flexibilität und Wartbarkeit**: Eine bewusste Exploration des Lösungsraums fördert [[Modularität]] und [[Erweiterbarkeit]], da Abhängigkeiten und Verantwortlichkeiten klar abgegrenzt werden.
- **Risikominimierung**: Durch die Abwägung von Trade-offs (z. B. zwischen [[Performance]] und [[Lesbarkeit]]) werden spätere Refactoring-Kosten reduziert.
- **Kommunikation im Team**: Der Lösungsraum bietet eine gemeinsame Sprache, um Design-Optionen zu diskutieren (z. B. im Rahmen von [[Architektur-Reviews]]).
- **Abgrenzung & Grenzen:** Der Lösungsraum ist abzugrenzen von:
- **Problemraum**: Beschreibt die Anforderungen und Rahmenbedingungen (z. B. Use Cases, [[User_Stories]]), ohne Lösungsvorschläge zu machen. Der Lösungsraum beginnt dort, wo der Problemraum endet.
- **Einzelnen Entwurfsmustern**: Während [[Entwurfsmuster]] wie [[Facade]] oder [[Strategy]] konkrete Lösungen innerhalb des Lösungsraums darstellen, ist der Lösungsraum selbst die übergeordnete Menge aller möglichen Muster und Nicht-Muster.
- **Stolpersteine**: 
  - **Über-Exploration**: Zu viele Alternativen können zu [[Analysis_Paralysis]] führen. Der Lösungsraum sollte durch [[Architekturprinzipien]] (z. B. [[KISS]]) eingegrenzt werden.
  - **Implizite Annahmen**: Unbewusste Einschränkungen (z. B. „Wir nutzen immer [[MVC]]“) können den Lösungsraum unnötig verkleinern.
  - **Technische Schulden**: Kurzfristige Entscheidungen (z. B. [[Quick_and_Dirty]]) verengen den Lösungsraum für zukünftige Iterationen.
- **Beispiel / Code:** ```mermaid
classDiagram
    class StilberaterSystem {
        +organisiereOutfit()
        +verwalteBenutzerdaten()
    }
    
    class OutfitGenerator {
        +generiereVorschlaege()
    }
    
    class Benutzerprofil {
        +speichereVorlieben()
        +ladeVorlieben()
    }
    
    class WetterAPI {
        +holeWetterdaten()
    }
    
    StilberaterSystem --> OutfitGenerator : verwaltet
    StilberaterSystem --> Benutzerprofil : verwaltet
    OutfitGenerator --> WetterAPI : nutzt
    OutfitGenerator --> Benutzerprofil : nutzt

    note for StilberaterSystem "Zentrale Klasse nach [[GRASP#Controller]]-Prinzip"
    note for OutfitGenerator "Hohe Kohäsion: Nur Outfit-Logik"
    note for WetterAPI "Lose Kopplung: Austauschbar via [[Schnittstelle]]"
```

**Alternativen im Lösungsraum für `MyStilberater`:**
1. **Zentrale Steuerung**: `StilberaterSystem` als [[Facade]] für alle Subsysteme (wie oben).
2. **Dezentrale Steuerung**: Jede Komponente (`OutfitGenerator`, `Benutzerprofil`) kommuniziert direkt via [[Observer_Pattern]].
3. **Event-Driven**: Nutzung eines [[Message_Broker]] (z. B. [[Event_Sourcing]]) zur Entkopplung.
