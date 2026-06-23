---
id: b7ed84b8-4727-499c-87b3-a4cb76d26803
title: "Realität"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - abstraktion
  - draft
source: "software_engineering_kapitel_03"
---

# [[Realität]]

- **Kernkonzept:** Realität bezeichnet im Kontext der objektorientierten Modellierung die Gesamtheit der Dinge, Personen oder abstrakten Begriffe der wahrnehmbaren oder gedachten Welt, die durch Objekte in einem Softwaresystem abgebildet werden sollen. Sie dient als Ausgangspunkt für die Abstraktion und Modellierung von Problembereichen.
- **Nutzen & Zweck:** Das Konzept der Realität ermöglicht es, komplexe Sachverhalte aus der echten Welt systematisch zu erfassen und in ein strukturiertes Modell zu überführen. Es löst das Problem, dass Softwareentwicklung oft reale Prozesse, Entitäten oder Beziehungen abbilden muss, ohne dabei die Komplexität der Wirklichkeit vollständig reproduzieren zu können. Durch die Fokussierung auf relevante Aspekte der Realität wird eine handhabbare Grundlage für Analyse, Design und Implementierung geschaffen.
- **Abgrenzung & Grenzen:** Das Konzept der Realität sollte nicht genutzt werden, wenn es um rein technische oder implementierungsnahe Fragestellungen geht, die keine direkte Entsprechung in der physischen oder konzeptuellen Welt haben. Es unterscheidet sich von rein datengetriebenen Ansätzen (z. B. relationalen Modellen), die oft auf Tabellenstrukturen basieren und keine direkte Abbildung realer Entitäten anstreben. Zudem ist die Realität als Ausgangspunkt ungeeignet, wenn das Problem keine klaren Entsprechungen in der echten Welt hat oder wenn eine zu starke Fokussierung auf Details die Abstraktion behindert.
- **Beispiel / Code:** ```java
// Beispiel: Abbildung eines realen Vereinsmitglieds als Klasse
class Mitglied {
    private String name;       // Abbildung des realen Attributs "Name"
    private String adresse;    // Abbildung des realen Attributs "Adresse"
    private int alter;         // Abbildung des realen Attributs "Alter"
    
    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
    }
    
    // Abbildung einer realen Fähigkeit (Leistungsprognose)
    public int leistungsprognose() {
        return alter * 10; // Vereinfachte Berechnung
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d4b
- **Vorgänger / Parent:** [[Abstraktion]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Modell]]
