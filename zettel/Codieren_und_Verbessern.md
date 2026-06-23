---
id: e894c6a5-2d29-4c13-b357-4336628113bd
title: "Codieren_und_Verbessern"
date: 2026-06-24
tags:
  - software_engineering
  - anti-pattern
  - ad-hoc
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Codieren_und_Verbessern]]

- **Kernkonzept:** Ein naiver [[Software-Entwicklungsansatz|Software-Entwicklungsansatz]] bzw. [[Ad-hoc_Ansatz]], bei dem [[Code]] ohne vorherige [[Anforderungsanalyse]], systematische [[Planung]] oder [[Design|Designphase]] geschrieben und iterativ verbessert wird. Dieser Ansatz dient als Negativbeispiel für die Notwendigkeit strukturierter [[Software-Entwicklungsprozess|Software-Entwicklungsprozesse]], kann jedoch in spezifischen Kontexten wie [[Prototyp|Prototypen]] oder [[Proof_of_Concept|Proof of Concepts]] kurzfristig eingesetzt werden.
- **Nutzen & Zweck:** Der Ansatz hat keinen expliziten Nutzen im Sinne professioneller [[Software-Entwicklung]], da er zu [[Technischer_Schuld]], [[Redundanz]] und [[Wartungsproblemen]] führt. Allerdings ermöglicht er in frühen Projektphasen oder bei kleinen [[Projekte|Projekten]] eine schnelle Umsetzung von [[Prototyp|Prototypen]] oder die Klärung von [[Forschungsfragen]], ohne den Overhead formaler [[Prozessmodelle]]. Für [[Produktionssoftware]] ist er jedoch ungeeignet.
- **Abgrenzung & Grenzen:** Der Ansatz führt zu unwartbarem [[Code]], hohen [[Wartungskosten]] und [[Technischer_Schuld]], da er keine strukturierte [[Anforderungsanalyse]], [[Design|Designphase]] oder [[Refactoring|Refactoring-Strategien]] vorsieht. Im Gegensatz zu etablierten [[Prozessmodelle|Prozessmodellen]] wie dem [[Wasserfallmodell]] oder [[Agile_Methodik|agilen Methoden]] fehlt eine systematische [[Planung]], was zu [[Redundanz]], inkonsistenten [[Schnittstelle|Schnittstellen]] und mangelnder [[Kohäsion]] führt. Besonders problematisch wird dies bei größeren [[Systemen]], wo [[Lose_Kopplung]] und klare [[Architektur]] entscheidend sind. Besser geeignet sind iterative Ansätze mit definierten [[Design|Designphasen]] und kontinuierlichem [[Refactoring]].
- **Beispiel / Code:** ```java
// Beispiel 1: Naiver Ansatz ohne Design (Bubble Sort)
public void sortiereDaten(int[] daten) {
    // Direkte Implementierung ohne Planung oder Optimierung
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

// Beispiel 2: Ad-hoc-Erweiterung ohne Refactoring (Calculator-Klasse)
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    
    // Später hinzugefügt, ohne Berücksichtigung von Design oder Konsistenz
    public int multiply(int a, int b) {
        return a * b;
    }
    
    // Weitere Methoden könnten inkonsistent hinzugefügt werden
    public double divide(int a, int b) {
        if (b == 0) {
            throw new IllegalArgumentException("Division durch Null");
        }
        return (double) a / b;
    }
}
```
