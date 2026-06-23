---
id: 147b5c3b-415a-45b1-88c7-3f10e3a21964
title: "Spiralmodell"
date: 2026-06-24
tags:
  - software_engineering
  - prozessmodelle
  - risikomanagement
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Spiralmodell]]

- **Kernkonzept:** Das [[Spiralmodell]] ist ein [[iteratives_Prozessmodell|iteratives]] und [[risikogetriebenes_Prozessmodell|risikogetriebenes]] [[Prozessmodell]] in der [[Softwareentwicklung]], das durch wiederholte [[Zyklen]] aus Planung, [[Risikoanalyse]], Entwicklung und Evaluation die schrittweise Verfeinerung eines [[System|Systems]] ermöglicht. Es kombiniert Elemente sequenzieller und prototypischer Vorgehensweisen, um frühzeitig [[Risiken]] zu identifizieren und zu mitigieren.
- **Nutzen & Zweck:** Das [[Spiralmodell]] existiert, um komplexe und risikobehaftete [[Softwareprojekte]] systematisch zu steuern, indem es Flexibilität für Änderungen bietet und gleichzeitig eine strukturierte Herangehensweise an [[Risikomanagement]] ermöglicht. Es löst das Problem starrer, linearer [[Prozessmodelle]] wie dem [[Wasserfallmodell]], die bei unklaren [[Anforderung|Anforderungen]] oder hohen technischen [[Risiken]] scheitern, indem es iterative Rückkopplungsschleifen einbaut und so [[Anpassung|Anpassungen]] während des Entwicklungsprozesses erlaubt. Zudem dient es als Grundlage für [[Agile_Entwicklung|agile]] und [[Moderne_Prozessmodelle|moderne Prozessmodelle]], da es iterative [[Evaluation]] und kontinuierliche Verbesserung fördert.
- **Abgrenzung & Grenzen:** Das [[Spiralmodell]] sollte nicht bei kleinen, klar definierten [[Projekte|Projekten]] mit geringem [[Risiko]] eingesetzt werden, da der hohe Aufwand für Planung und [[Risikoanalyse]] in solchen Fällen ineffizient ist. Es unterscheidet sich von [[Agile_Entwicklung|agilen Modellen]] wie [[Scrum]] durch seinen expliziten Fokus auf [[Risikomanagement]] und formale Evaluationsphasen, während agile Ansätze stärker auf kontinuierliche Lieferung und [[Kundeneinbindung]] setzen. Zudem ist es weniger geeignet für [[Projekte]] mit festen Budgets oder Zeitplänen, da die iterative Natur zu unvorhersehbaren Kosten führen kann. Im Vergleich zum [[Wasserfallmodell]] oder [[Prototypmodell]] ist es komplexer, bietet jedoch durch seinen Fokus auf [[Risikoanalyse]] eine robustere Grundlage für risikobehaftete Vorhaben.
- **Beispiel / Code:** ```java
// Pseudocode zur Illustration eines Spiralmodell-Zyklus
public class SpiralModelCycle {
    public void executeCycle() {
        // 1. Planung: Ziele, Alternativen, Randbedingungen festlegen
        Plan plan = defineObjectivesAndConstraints();
        
        // 2. Risikoanalyse: Risiken identifizieren und bewerten
        List<Risk> risks = identifyRisks(plan);
        evaluateRisks(risks);
        
        // 3. Entwicklung und Test: Prototyp oder Teilprodukt erstellen
        Prototype prototype = developPrototype(plan);
        testPrototype(prototype);
        
        // 4. Evaluation: Ergebnisse prüfen und nächsten Zyklus planen
        ReviewResult result = reviewCycleResults(prototype, risks);
        if (!result.isFinal()) {
            executeCycle(); // Nächster Zyklus
        }
    }
    
    // Beispiel für Risikoanalyse-Methode
    private void evaluateRisks(List<Risk> risks) {
        for (Risk risk : risks) {
            if (risk.getSeverity() > THRESHOLD) {
                applyMitigationStrategy(risk);
            }
        }
    }
}

// Beispiel für Spiralmodell-Zyklus in textueller Form:
// 1. Ziele und Alternativen festlegen
// 2. Risiken identifizieren und bewerten
// 3. Entwicklung und Test des Prototyps
// 4. Planung des nächsten Zyklus
```
