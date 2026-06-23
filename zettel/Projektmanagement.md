---
id: 9bf295c2-ff35-4d14-9d12-5e9d2ce13dac
title: "Projektmanagement"
date: 2026-06-23
tags:
  - software_engineering
  - management
  - planung
  - draft
source: "software_engineering_kapitel_06"
---

# [[Projektmanagement]]

- **Kernkonzept:** Projektmanagement im Software-Engineering bezeichnet die systematische Planung, Steuerung und Kontrolle von Softwareprojekten, um definierte Ziele innerhalb festgelegter Zeit-, Kosten- und Qualitätsvorgaben zu erreichen. Es umfasst die Organisation von Iterationen, die Zuweisung von Ressourcen und die kontinuierliche Abstimmung mit Stakeholdern.
- **Nutzen & Zweck:** Projektmanagement löst das Problem der Komplexität und Unsicherheit in Softwareprojekten, indem es klare Strukturen, Meilensteine und Verantwortlichkeiten schafft. Es ermöglicht die frühzeitige Identifikation von Risiken, die effiziente Nutzung von Ressourcen und die transparente Kommunikation zwischen Entwicklern, Auftraggebern und anderen Beteiligten, um termingerechte und qualitativ hochwertige Ergebnisse zu liefern.
- **Abgrenzung & Grenzen:** Projektmanagement sollte nicht in hochgradig unklaren oder explorativen Projekten eingesetzt werden, bei denen Anforderungen und Ziele sich ständig ändern und keine stabilen Rahmenbedingungen existieren. Es unterscheidet sich von Ad-hoc-Entwicklung durch seine strukturierte Vorgehensweise und von reinen agilen Methoden wie Kanban durch die Betonung fester Iterationen (z. B. Sprints) und formalisierter Planungsschritte. Bei sehr kleinen Projekten oder Einzelentwicklern kann der Overhead des Projektmanagements unnötig sein.
- **Beispiel / Code:** ```java
// Beispiel für einen einfachen Projektplan als Java-Klasse (vereinfacht)
public class ProjektPlan {
    private String projektName;
    private List<Iteration> iterationen;
    private List<Meilenstein> meilensteine;
    
    public ProjektPlan(String projektName) {
        this.projektName = projektName;
        this.iterationen = new ArrayList<>();
        this.meilensteine = new ArrayList<>();
    }
    
    public void iterationHinzufuegen(Iteration iteration) {
        iterationen.add(iteration);
        if (iteration.istMeilenstein()) {
            meilensteine.add(new Meilenstein(iteration.getEndDatum(), iteration.getZiel()));
        }
    }
    
    public void projektStatusAusgeben() {
        System.out.println("Projekt: " + projektName);
        System.out.println("Anzahl Iterationen: " + iterationen.size());
        System.out.println("Meilensteine:");
        meilensteine.forEach(m -> System.out.println("- " + m.getDatum() + ": " + m.getZiel()));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1g
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Netzplan]]
  - [[Meilensteine]]
  - [[Zeitplanung]]
  - [[Ressourcenplanung]]
  - [[Risikomanagement]]
- **Querverweise:** keine
