---
id: 82819ad3-b1f6-48dc-a125-98993b02e105
title: "Petri-Netz Semantik"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - prozess
  - draft
source: "software_engineering_kapitel_08"
---

# [[Petri-Netz Semantik]]

- **Kernkonzept:** Petri-Netz Semantik beschreibt eine formale Methode zur Modellierung von parallelen, asynchronen und verteilten Prozessen in Aktivitätsdiagrammen der UML. Sie ermöglicht die präzise Darstellung von Zustandsübergängen, Synchronisation und Nebenläufigkeit durch Plätze, Transitionen und Marken.
- **Nutzen & Zweck:** Dieses Konzept existiert, um komplexe Abläufe mit parallelen oder konkurrierenden Prozessen exakt zu modellieren und zu analysieren. Es löst das Problem der Mehrdeutigkeit in der Darstellung von Nebenläufigkeit und Synchronisation, indem es eine mathematisch fundierte Grundlage für die Verifikation von Prozessmodellen bietet. Besonders nützlich ist es in der Softwareentwicklung, um Workflows, Algorithmen oder Systeminteraktionen mit klaren Regeln für Zustandsänderungen abzubilden.
- **Abgrenzung & Grenzen:** Petri-Netz Semantik sollte nicht genutzt werden, wenn einfache, lineare Abläufe ohne Parallelität oder Synchronisation modelliert werden sollen, da der Aufwand für die formale Darstellung dann unnötig hoch ist. Alternativen wie einfache Flussdiagramme oder sequentielle Aktivitätsdiagramme sind hier effizienter. Zudem eignet es sich weniger für die Darstellung von hierarchischen oder stark strukturierten Prozessen, bei denen objektorientierte Ansätze oder Zustandsdiagramme besser geeignet sind. Die Komplexität von Petri-Netzen kann zudem die Verständlichkeit für nicht-technische Stakeholder erschweren.
- **Beispiel / Code:** ```java
// Vereinfachte Darstellung eines Petri-Netzes in UML-Aktivitätsdiagramm-Notation
// (kein direkter Code, aber strukturelle Analogie)

class PetriNet {
    List<Place> places;      // Zustände (z. B. "Daten bereit")
    List<Transition> transitions; // Ereignisse (z. B. "Verarbeite Daten")
    List<Token> tokens;      // Marken zur Steuerung der Ausführung
    
    void fireTransition(Transition t) {
        if (t.canFire()) {       // Prüft, ob alle Eingangsplätze Marken haben
            t.consumeTokens();   // Entfernt Marken aus Eingangsplätzen
            t.produceTokens();   // Fügt Marken zu Ausgangsplätzen hinzu
        }
    }
}

// Beispiel: Synchronisation zweier paralleler Prozesse
// Transition "Merge" feuert erst, wenn beide Eingangsplätze Marken enthalten.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7a
- **Vorgänger / Parent:** [[Petri-Netz]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Aktivitätsdiagramm_Semantik]]
