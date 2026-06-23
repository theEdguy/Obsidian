---
id: 2ae432b1-eae4-4c7f-93bd-c95bc68d369f
title: "Anforderungsvalidierung"
date: 2026-06-23
tags:
  - software_engineering
  - validierung
  - anforderungen
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Anforderungsvalidierung]]

- **Kernkonzept:** Die [[Anforderungsvalidierung]] ist der systematische [[Prozess]], um sicherzustellen, dass die erfassten [[Anforderung|Anforderungen]] an ein [[Softwaresystem]] korrekt, vollständig und konsistent sind sowie den tatsächlichen [[Bedürfnis|Bedürfnissen]] der [[Stakeholder]] entsprechen. Sie dient als [[Qualitätssicherung]] vor der Umsetzung in [[Design]] und [[Implementierung]] und ist ein zentraler Bestandteil des [[Requirements_Engineering|Requirements Engineerings]].
- **Nutzen & Zweck:** Dieses Konzept existiert, um frühzeitig [[Missverständnis|Missverständnisse]], Lücken oder [[Widerspruch|Widersprüche]] in den [[Anforderung|Anforderungen]] zu identifizieren und zu beheben. Dadurch werden teure Nacharbeiten in späteren [[Entwicklungsphase|Entwicklungsphasen]] vermieden, die [[Projektziel|Projektziele]] klarer definiert und die [[Akzeptanz]] des Endprodukts bei den [[Nutzer|Nutzern]] und [[Stakeholder|Stakeholdern]] erhöht. Ohne [[Validierung]] besteht das Risiko, dass das entwickelte [[System]] nicht den tatsächlichen [[Anforderung|Anforderungen]] entspricht, was zu [[Funktionsmangel|Funktionsmängeln]] oder Ablehnung durch die [[Anwender]] führen kann. Die [[Anforderungsvalidierung]] stellt zudem sicher, dass die [[Anforderung|Anforderungen]] die [[Geschäftsprozess|Geschäftsprozesse]] und [[Nutzerbedürfnis|Nutzerbedürfnisse]] korrekt abbilden und trägt zur [[Risikominimierung]] bei.
- **Abgrenzung & Grenzen:** Die [[Anforderungsvalidierung]] sollte nicht mit der [[Anforderungserhebung]] oder [[Anforderungsanalyse]] verwechselt werden, da sie erst nach der initialen Erfassung der [[Anforderung|Anforderungen]] erfolgt und deren Überprüfung auf [[Korrektheit]], [[Vollständigkeit]] und [[Konsistenz]] fokussiert. Sie ist kein Ersatz für spätere [[Testphase|Testphasen]] wie [[Systemtest|Systemtests]] oder [[Abnahmetest|Abnahmetests]], da diese die korrekte [[Umsetzung]] der [[Anforderung|Anforderungen]] prüfen, nicht deren [[Gültigkeit]]. Alternativen wie informelle [[Review]]s oder reine [[Dokumentenprüfung|Dokumentenprüfungen]] können weniger strukturiert sein und kritische [[Fehler]] übersehen. Die [[Validierung]] ist zudem nicht sinnvoll, wenn die [[Anforderung|Anforderungen]] bereits final umgesetzt wurden oder keine [[Stakeholder]] für [[Feedback]] verfügbar sind. Sie ist ein iterativer [[Prozess]], der während des gesamten [[Requirements_Engineering|Requirements Engineerings]] stattfindet und nicht als einmalige Aktivität betrachtet werden sollte.
- **Beispiel / Code:** ```java
// Beispiel für eine strukturierte Validierungscheckliste mit erweiterten Prüfungen (Pseudocode)
public class Anforderungsvalidierung {
    public static boolean validiereAnforderungen(Anforderung[] anforderungen) {
        boolean istKorrekt = true;
        
        // 1. Prüfung auf Vollständigkeit
        for (Anforderung anf : anforderungen) {
            if (anf.getBeschreibung() == null || anf.getBeschreibung().isEmpty()) {
                System.err.println("Fehler: Anforderung " + anf.getId() + " hat keine Beschreibung.");
                istKorrekt = false;
            }
            if (anf.getStakeholder() == null) {
                System.err.println("Fehler: Anforderung " + anf.getId() + " hat keinen [[Stakeholder|Stakeholder]] zugeordnet.");
                istKorrekt = false;
            }
        }
        
        // 2. Prüfung auf Konsistenz (z. B. keine widersprüchlichen Anforderungen)
        for (int i = 0; i < anforderungen.length; i++) {
            for (int j = i + 1; j < anforderungen.length; j++) {
                if (anforderungen[i].widerspricht(anforderungen[j])) {
                    System.err.println("Widerspruch: Anforderung " + anforderungen[i].getId() +
                                      " kollidiert mit " + anforderungen[j].getId());
                    istKorrekt = false;
                }
            }
        }
        
        // 3. Prüfung auf Traceability (Zuordnung zu Use Cases und Geschäftsprozessen)
        for (Anforderung anf : anforderungen) {
            if (anf.getUseCaseReferenz() == null) {
                System.err.println("Warnung: Anforderung " + anf.getId() +
                                  " ist keinem [[Use_Case|Use Case]] zugeordnet.");
            }
            if (anf.getGeschaeftsprozessReferenz() == null) {
                System.err.println("Warnung: Anforderung " + anf.getId() +
                                  " ist keinem [[Geschäftsprozess]] zugeordnet.");
            }
        }
        
        // 4. Prüfung auf Testbarkeit
        for (Anforderung anf : anforderungen) {
            if (!anf.istTestbar()) {
                System.err.println("Fehler: Anforderung " + anf.getId() +
                                  " ist nicht testbar (z. B. unklare Akzeptanzkriterien).");
                istKorrekt = false;
            }
        }
        
        return istKorrekt;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4c
- **Vorgänger / Parent:** [[Anforderungsanalyse]]
- **Folgezettel / Unterzettel:**
  - [[Review]]
  - [[Prototyping]]
  - [[Test]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Qualitätssicherung]]
