---
id: 01be843f-710b-46ac-ac9a-d9e97fd83c5e
title: "Qualitative_und_Quantitative_Fragestellungen"
date: 2026-06-24
tags:
  - software_engineering
  - empirie
  - metriken
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Qualitative_und_Quantitative_Fragestellungen]]

- **Kernkonzept:** Untersuchung von [[Verhalten]], [[Meinungen]] und [[Motivationen]] in der [[Software-Entwicklung]] durch offene [[Fragestellung|Fragen]] und interpretative [[Analyse]] (qualitativ) sowie Messung von [[Ereignissen]], [[Korrelationen]] und [[Zusammenhängen]] durch geschlossene [[Fragestellung|Fragen]] und statistische [[Analyse]] (quantitativ). Beide Ansätze ergänzen sich in der [[empirischen_Forschung|empirischen Forschung]] zur ganzheitlichen Erfassung von [[Anforderungen]] und [[Systemverhalten]].
- **Nutzen & Zweck:** Qualitative [[Fragestellung|Fragestellungen]] dienen dem Verständnis von [[Kontext]], [[Nutzerbedürfnissen]] und [[Motivationen]], um [[Anforderungen]] präziser zu erfassen und [[Usability]] zu verbessern. Sie sind essenziell für [[Domain-Driven_Design]] und [[User_Centered_Design]]. Quantitative [[Fragestellung|Fragestellungen]] ermöglichen dagegen eine objektive [[Bewertung]] von [[Performance]], [[Fehlerraten]] oder [[Nutzerakzeptanz]] und bilden die Grundlage für [[KPIs]] und datengetriebene [[Entscheidung|Entscheidungen]]. Beide Ansätze zusammen unterstützen eine fundierte [[Anforderungsanalyse]] und [[Systemoptimierung]].
- **Abgrenzung & Grenzen:** Qualitative und quantitative [[Fragestellung|Fragestellungen]] sind komplementär, aber nicht austauschbar. Qualitative Ansätze erklären das "Warum?" hinter [[Verhalten]] und [[Motivationen]], sind jedoch nicht für statistische Aussagen geeignet. Quantitative Ansätze messen das "Wie viel?", liefern aber keine Erklärungen für [[Ursache|Ursachen]] oder [[Motivation]]. Qualitative Methoden eignen sich nicht für [[Performance-Optimierung]] oder [[Skalierbarkeit]]-Analysen, während quantitative Methoden keine tiefgehenden [[Usability]]-Tests oder [[Domain-Analyse|Domain-Analysen]] ersetzen können. Beide Ansätze erfordern unterschiedliche [[Forschungsdesign|Forschungsdesigns]] und [[Datenanalyse|Datenanalysen]].
- **Beispiel / Code:** ```text
// Beispiel für qualitative Datenerhebung (Interviewleitfaden)
1. Wie bewerten Sie die [[Benutzerfreundlichkeit]] des [[System|Systems]]?
2. Welche [[Herausforderung|Herausforderungen]] sehen Sie bei der Nutzung?
3. Warum bevorzugen Sie [[Lösung_A|Lösung A]] gegenüber [[Lösung_B|Lösung B]]?
```

```java
// Beispiel für quantitative Datenerhebung (Metrik)
public class BugTracker {
    private int totalBugs;
    private int resolvedBugs;
    
    public double getResolutionRate() {
        return (double) resolvedBugs / totalBugs * 100;
    }
}
```
