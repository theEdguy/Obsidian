---
id: 7dd6079f-7edc-4b95-a3bf-b09baead8b32
title: "Methodische_Durchgängigkeit"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - architektur
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Methodische_Durchgängigkeit]]

- **Kernkonzept:** Die [[Methodische_Durchgängigkeit]] beschreibt die nahtlose Übertragung von [[Anforderung|Anforderungen]] aus dem [[Problemraum]] in den [[Lösungsraum]] durch konsistente [[Modellierung]] und [[Implementierung]]. Sie stellt sicher, dass [[Analyse]]-Ergebnisse direkt in [[Software]]-Strukturen überführt werden.
- **Nutzen & Zweck:** Sie löst das Problem der [[Semantische_Lücke|semantischen Lücke]] zwischen [[Anforderung|Anforderungen]] und [[Implementierung]], indem sie eine durchgängige [[Abstraktionsebene]] von der [[Analyse]] bis zum [[Code]] schafft. Dies verbessert die [[Konsistenz]] und [[Wartbarkeit]] von [[Software]]-Systemen.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Prototyping|Prototypen]] mit unklaren [[Anforderung|Anforderungen]] oder bei stark explorativen [[Entwicklungsprozess|Entwicklungsprozessen]], da sie eine stabile [[Modellierung]] voraussetzt. Unterscheidet sich von [[Ad-hoc_Entwicklung]] durch systematische [[Dokumentation]] und [[Traceability]].
- **Beispiel / Code:** ```java
// Analyse: UML-Klasse "Mitglied"
// Mitglied (name: Text, adresse: Text, alter: Datum, leistung: Punkte)

// Implementierung: Java-Klasse
class Mitglied {
    private String name;
    private Anschrift adresse;
    private Date alter;
    private int leistung;

    public int leistungsprognose(Date datum) {
        // Implementierungslogik
    }
}
```
