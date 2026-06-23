---
id: 0cadcba9-e96e-4297-b154-2f746950d84c
title: "Metriken"
date: 2026-06-23
tags:
  - software_engineering
  - messung
  - qualität
  - draft
source: "software_engineering_kapitel_06"
---

# [[Metriken]]

- **Kernkonzept:** Metriken sind quantifizierbare Messgrößen, die verwendet werden, um nicht-funktionale Anforderungen wie Leistung, Zuverlässigkeit oder Wartbarkeit objektiv bewertbar und überprüfbar zu machen. Sie ermöglichen die Transformation subjektiver Qualitätskriterien in messbare Zielvorgaben.
- **Nutzen & Zweck:** Metriken existieren, um die Erfüllung nicht-funktionaler Anforderungen nachvollziehbar und vergleichbar zu gestalten. Ohne sie wären Qualitätsmerkmale wie Performance oder Sicherheit interpretationsabhängig und könnten nicht systematisch überprüft oder verbessert werden. Sie lösen das Problem der Subjektivität in der Bewertung von Softwareeigenschaften und schaffen eine Grundlage für fundierte Entscheidungen im Entwicklungsprozess.
- **Abgrenzung & Grenzen:** Metriken sollten nicht genutzt werden, wenn Anforderungen bereits objektiv und binär überprüfbar sind (z. B. funktionale Anforderungen wie 'Das System muss eine Login-Funktion bieten'). Sie sind ungeeignet für qualitative Aspekte, die sich nicht sinnvoll quantifizieren lassen (z. B. ästhetische Designfragen). Im Gegensatz zu rein beschreibenden Anforderungen (z. B. 'Das System soll benutzerfreundlich sein') erfordern Metriken präzise Definitionen und Messverfahren, was zusätzlichen Aufwand bedeutet.
- **Beispiel / Code:** ```java
// Beispiel: Metrik zur Messung der Antwortzeit (Performance)
public class PerformanceMetric {
    private long startTime;
    private long endTime;

    public void startMeasurement() {
        startTime = System.currentTimeMillis();
    }

    public void endMeasurement() {
        endTime = System.currentTimeMillis();
    }

    public long getResponseTime() {
        return endTime - startTime; // Antwortzeit in Millisekunden
    }
}

// Nutzung:
PerformanceMetric metric = new PerformanceMetric();
metric.startMeasurement();
// ... (Ausführung der zu messenden Operation)
metric.endMeasurement();
System.out.println("Antwortzeit: " + metric.getResponseTime() + " ms");
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a2a
- **Vorgänger / Parent:** [[Nicht-funktionale_Anforderungen]]
- **Folgezettel / Unterzettel:**
  - [[Leistungsmetriken]]
  - [[Zuverlässigkeitsmetriken]]
  - [[Sicherheitsmetriken]]
- **Querverweise:** keine
