---
id: f2e58798-82ca-44e6-a193-acf208cb7884
title: "Loesungsraum"
date: 2026-05-31
tags:
  - software_engineering
  - softwareentwurf
  - entwurfsmuster
  - architekturmuster
  - systemdesign
  - trade-offs
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Loesungsraum]]

- **Kernkonzept:** Der **Lösungsraum** bezeichnet im Kontext des [[Softwareentwurfs]] die Menge aller möglichen Design- und Implementierungsvarianten, die ein gegebenes Problem oder eine Anforderung erfüllen können. Er umfasst strukturelle und verhaltensbezogene Alternativen, die durch [[Entwurfsmuster]], [[Architekturmuster]] oder [[Modularisierung]] realisiert werden können. Der Lösungsraum ist dynamisch und wird durch Rahmenbedingungen wie [[Kopplung]], [[Kohäsion]], Performance-Anforderungen oder technologische Einschränkungen eingegrenzt.
- **Nutzen & Zweck:** Der Lösungsraum dient als analytisches Werkzeug, um:
- **Design-Entscheidungen systematisch zu explorieren** (z. B. Abwägung zwischen [[Fassade_Pattern]] und [[Mediator_Pattern]] für die Systemorganisation).
- **Trade-offs zu visualisieren** (z. B. Flexibilität vs. Komplexität bei der Wahl zwischen [[Plugin-Architektur]] und monolithischer Struktur).
- **Kreativität im Entwurf zu fördern**, indem bewusst mehrere Lösungswege verglichen werden (z. B. [[Event-Driven_Architecture]] vs. [[Request-Response]]).
- **Risiken zu minimieren**, indem frühzeitig alternative Pfade identifiziert werden, falls primäre Lösungen scheitern (z. B. Ersatz eines [[Singleton]] durch [[Dependency_Injection]] bei Testbarkeit).
- **Abgrenzung & Grenzen:** - **Kein Problemraum**: Der Lösungsraum setzt voraus, dass das Problem bereits durch [[Anforderungsanalyse]] oder [[Use_Cases]] definiert ist. Eine Vermischung führt zu unklaren Design-Entscheidungen.
- **Keine Implementierung**: Der Lösungsraum beschreibt *mögliche* Lösungen, nicht deren konkrete Umsetzung (z. B. Code oder [[Klassendiagramm]]).
- **Eingeschränkte Allgemeingültigkeit**: Lösungsräume sind kontextabhängig (z. B. ist [[Microservices]] im Embedded-Bereich oft ungeeignet).
- **Stolpersteine**: 
  - *Über-Exploration*: Zu viele Alternativen können zu [[Analysis_Paralysis]] führen.
  - *Voreingenommenheit*: Präferenzen für bestimmte [[Entwurfsmuster]] (z. B. [[Factory_Method]]) können den Lösungsraum unbewusst verengen.
  - *Fehlende Metriken*: Ohne klare Kriterien (z. B. [[Zyklomatische_Komplexität]], [[Kopplungsmetriken]]) ist die Bewertung von Alternativen subjektiv.
- **Beispiel / Code:** ```mermaid
classDiagram
    %% Beispiel: Lösungsraum für die Organisation eines mobilen Stilberaters (MyStilberater)
    %% Alternative 1: Zentrale Steuerung (Fassade)
    class StilberaterFassade {
        +empfehleOutfit()
        +speichereBenutzerdaten()
    }
    StilberaterFassade --> OutfitGenerator
    StilberaterFassade --> Benutzerverwaltung

    %% Alternative 2: Dezentrale Verantwortung (Mediator)
    class StilberaterMediator {
        +koordiniereEmpfehlung()
    }
    StilberaterMediator --> OutfitGenerator
    StilberaterMediator --> Benutzerverwaltung
    OutfitGenerator --> StilberaterMediator : Benachrichtigung
    Benutzerverwaltung --> StilberaterMediator : Benachrichtigung

    %% Gemeinsame Komponenten
    class OutfitGenerator {
        +generiereOutfit()
    }
    class Benutzerverwaltung {
        +speichereDaten()
        +lieferePräferenzen()
    }
```

**Erläuterung**:
- Die beiden Alternativen zeigen unterschiedliche Lösungen für die Systemorganisation:
  1. **Fassade**: Eine zentrale Klasse (`StilberaterFassade`) kapselt die Interaktion mit Subsystemen ([[Fassade_Pattern]]).
  2. **Mediator**: Eine vermittelnde Klasse (`StilberaterMediator`) reduziert direkte Abhängigkeiten zwischen Komponenten ([[Mediator_Pattern]]).
- Der Lösungsraum umfasst hier auch hybride Ansätze (z. B. Kombination beider Muster) oder weitere Varianten wie [[Event_Sourcing]].
