---
id: 5f98c0a2-63b1-4eb6-ba09-7a4862ac1015
title: "Iterativer Prozess"
date: 2026-06-23
tags:
  - software_engineering
  - prozess
  - draft
source: "software_engineering_kapitel_03"
---

# [[Iterativer Prozess]]

- **Kernkonzept:** Der iterative Prozess ist ein Vorgehensmodell in der Softwareentwicklung, bei dem das Projekt in wiederholte Zyklen (Iterationen) unterteilt wird. Jede Iteration umfasst Analyse, Design, Implementierung und Testen, um schrittweise ein funktionsfähiges Teilprodukt zu liefern.
- **Nutzen & Zweck:** Dieses Konzept existiert, um flexibel auf Änderungen in Anforderungen, Technologien oder Rahmenbedingungen reagieren zu können. Es löst das Problem starrer, linearer Entwicklungsmodelle (wie dem Wasserfallmodell), indem es frühzeitiges Feedback ermöglicht, Risiken reduziert und die Anpassungsfähigkeit an neue Erkenntnisse oder Prioritäten sicherstellt. Zudem fördert es die kontinuierliche Verbesserung der Softwarequalität und die schrittweise Integration von Teillösungen zu einem kohärenten Gesamtsystem.
- **Abgrenzung & Grenzen:** Der iterative Prozess sollte nicht genutzt werden, wenn Anforderungen von Anfang an vollständig und unveränderlich feststehen oder wenn Projekte extrem kurzlebig sind (z. B. einfache Prototypen). Im Vergleich zu sequenziellen Modellen erfordert er höheren Kommunikationsaufwand und kontinuierliche Abstimmung zwischen Stakeholdern. Alternativen wie das Wasserfallmodell sind bei klar definierten, stabilen Anforderungen effizienter, während agile Methoden (z. B. Scrum) noch stärker auf Selbstorganisation und kürzere Iterationen setzen.
- **Beispiel / Code:** ```java
// Beispiel: Iterative Entwicklung einer Mitgliedsklasse in mehreren Zyklen
// Iteration 1: Grundgerüst
class Mitglied {
    private String name;
    
    public Mitglied(String name) {
        this.name = name;
    }
}

// Iteration 2: Erweiterung um Attribute
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    
    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
    }
}

// Iteration 3: Hinzufügen von Methoden
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistung;
    
    public int leistungsprognose(int tage) {
        return this.leistung * tage; // Vereinfachte Berechnung
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Agile_Anpassung]]
- **Querverweise:** keine
