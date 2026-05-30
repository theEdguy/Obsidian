---
id: beb5f8e1-ea75-442b-8ebc-bbc78af8bb5b
title: "Codieren_und_Verbessern"
date: 2026-05-30
tags:
  - software_engineering
  - anti-pattern
  - software_entwicklung
  - draft
source: "SWE Slides (Folien 16-30)"
---

# [[Codieren_und_Verbessern]]

- **Kernkonzept:** Ein naiver [[Software-Entwicklungsansatz|Software-Entwicklungsansatz]], bei dem [[Code|Code]] ohne vorherige [[Anforderungsanalyse|Anforderungsanalyse]] oder [[Design|Design]] geschrieben und iterativ verbessert wird.
- **Nutzen & Zweck:** Kein expliziter Nutzen; dient als Negativbeispiel für die Notwendigkeit strukturierter [[Software-Entwicklungsprozess|Software-Entwicklungsprozesse]].
- **Abgrenzung & Grenzen:** Führt zu unwartbarem [[Code|Code]], hohen [[Wartungskosten|Wartungskosten]] und [[Technische_Schuld|technischer Schuld]]. Besser: [[Wasserfallmodell|Wasserfall]] oder [[Agile_Methodik|agile Methoden]] mit [[Design|Design]]-Phase.
- **Beispiel / Code:** ```java
// Beispiel: Naiver Ansatz ohne Design
public void sortiereDaten(int[] daten) {
    // Direkte Implementierung ohne Planung
    for (int i = 0; i < daten.length; i++) {
        for (int j = 0; j < daten.length - 1; j++) {
            if (daten[j] > daten[j + 1]) {
                int temp = daten[j];
                daten[j] = daten[j + 1];
                daten[j + 1] = temp;
            }
        }
    }
}
```
