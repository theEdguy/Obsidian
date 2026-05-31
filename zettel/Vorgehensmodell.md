---
id: 46a03deb-bc6b-42dd-8190-e7b82f1ea2f3
title: "Vorgehensmodell"
date: 2026-05-31
tags:
  - software_engineering
  - softwareprozess
  - projektmanagement
  - agile_methoden
  - uml
  - anforderungsanalyse
  - draft
source: "Klausur_Referenz"
---

# [[Vorgehensmodell]]

- **Kernkonzept:** Ein **Vorgehensmodell** ist ein strukturierter Rahmen im [[Software_Engineering]], der die Phasen, Aktivitäten, Rollen und Artefakte eines Softwareentwicklungsprozesses definiert. Es dient als Leitfaden für die systematische Planung, Durchführung und Kontrolle von Projekten. Vorgehensmodelle lassen sich grob in **klassische (planbasierte)** und **agile** Ansätze unterteilen, wobei erstere (z. B. das [[Wasserfallmodell]]) sequenziell und dokumentengetrieben arbeiten, während letztere (z. B. [[Scrum]] oder [[Extreme_Programming]]) iterativ, flexibel und kundenorientiert vorgehen.
- **Nutzen & Zweck:** Vorgehensmodelle bieten folgende Vorteile:
- **Strukturierung**: Klare Abläufe reduzieren Komplexität und verbessern die Nachvollziehbarkeit.
- **Risikominimierung**: Durch definierte Meilensteine (z. B. im [[V-Modell]]) oder kontinuierliches Feedback (agile Modelle) werden Fehler früh erkannt.
- **Kommunikation**: Standardisierte Artefakte (z. B. [[Use_Case_Diagramm]], [[Aktivitätsdiagramm]]) erleichtern die Abstimmung zwischen Stakeholdern.
- **Anpassbarkeit**: Agile Modelle ermöglichen die Integration neuer Anforderungen während des Projekts (z. B. durch [[Backlog_Refinement]] in Scrum).
- **Qualitätssicherung**: Phasen wie Testen oder Review sind explizit verankert (z. B. im [[Spiralmodell]]).
- **Abgrenzung & Grenzen:** 1. **Klassische vs. agile Modelle**: 
   - Klassische Modelle (z. B. Wasserfall) setzen auf vollständige Spezifikation zu Projektbeginn und sind ungeeignet für dynamische Umgebungen.
   - Agile Modelle (z. B. Scrum) erfordern hohe Disziplin und kontinuierliche Kundenbeteiligung, was in starren Organisationen schwer umsetzbar ist.
2. **Stolpersteine**:
   - **Überdokumentation**: Klassische Modelle können zu bürokratischen Hürden führen.
   - **Fehlende Flexibilität**: Agile Modelle scheitern oft an unklaren Prioritäten oder mangelnder Teamautonomie.
   - **Hybride Ansätze**: Kombinationen (z. B. [[SAFe]]) sind komplex und erfordern Erfahrung.
3. **Grenzen**:
   - Kein Modell garantiert Erfolg – entscheidend sind Teamkompetenz und Projektkontext.
   - Vorgehensmodelle sind **keine** [[Entwurfsmuster]] oder technische Lösungen, sondern organisatorische Rahmenwerke.
- **Beispiel / Code:** ```mermaid
flowchart TD
    A[Anforderungsanalyse] --> B[Systemdesign]
    B --> C[Implementierung]
    C --> D[Testen]
    D --> E[Auslieferung]
    
    subgraph Wasserfallmodell
    A --> B --> C --> D --> E
    end
    
    subgraph Scrum
    F[Sprint Planning] --> G[Sprint Backlog]
    G --> H[Daily Scrum]
    H --> I[Sprint Review]
    I --> J[Sprint Retrospective]
    J --> F
    end
```

**Erläuterung**:
- Das **Wasserfallmodell** zeigt eine lineare Abfolge, bei der jede Phase abgeschlossen sein muss, bevor die nächste beginnt.
- **Scrum** visualisiert einen iterativen Zyklus mit festen Zeitabschnitten (Sprints) und kontinuierlichem Feedback.
