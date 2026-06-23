---
id: b2702054-76f3-4ffe-b3d3-2e48865be9bc
title: "Objektorientierung als durchgängiges Stilmittel"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - paradigma
  - draft
source: "software_engineering_kapitel_03"
---

# [[Objektorientierung als durchgängiges Stilmittel]]

- **Kernkonzept:** Objektorientierung als durchgängiges Stilmittel bezeichnet die konsistente Anwendung objektorientierter Prinzipien – wie Kapselung, Daten und Verhalten, Vererbung und Polymorphie – über alle Ebenen der Softwareentwicklung hinweg, von der Analyse über das Design bis zur Implementierung und Architektur.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem inkonsistenter oder fragmentierter Softwaremodelle, indem es eine einheitliche Sprache und Methodik für die Abbildung realer Probleme in technische Lösungen bereitstellt. Es verbessert die Nachvollziehbarkeit, Wartbarkeit und Erweiterbarkeit von Systemen, da Konzepte wie Klassen, Objekte und Beziehungen durchgängig vom Problemraum (Anforderungen) bis zum Lösungsraum (Code) übertragen werden können. Zudem fördert es die Kommunikation zwischen Stakeholdern, da Modelle und Implementierung auf denselben Prinzipien basieren.
- **Abgrenzung & Grenzen:** Objektorientierung als durchgängiges Stilmittel sollte nicht eingesetzt werden, wenn das Problem oder die Domäne besser durch andere Paradigmen – wie funktionale Programmierung (z. B. bei mathematischen Transformationen) oder prozedurale Ansätze (z. B. bei performancekritischen Algorithmen) – abgebildet werden kann. Es eignet sich weniger für Systeme, die stark auf Datenflüsse oder zustandslose Operationen fokussieren, da der Overhead der Objektmodellierung hier unnötig komplex sein kann. Zudem erfordert die durchgängige Anwendung Disziplin und Schulung, da sie bei unsachgemäßer Nutzung zu übermäßig verschachtelten oder schwer verständlichen Architekturen führen kann.
- **Beispiel / Code:** ```java
// Durchgängige Modellierung: Klasse aus der Analyse (UML) wird direkt in Code überführt
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistungspunkte;

    // Operation aus dem Analysemodell
    public int leistungsprognose(int tage) {
        return this.leistungspunkte * tage / 365;
    }
}

// Verwendung in der Architektur (z. B. als Komponente)
class Vereinsverwaltung {
    private List<Mitglied> mitglieder;

    public void aktualisiereMitgliederleistung() {
        for (Mitglied m : mitglieder) {
            int prognose = m.leistungsprognose(90); // Durchgängige Nutzung der Operation
            System.out.println(m.name + ": " + prognose + " Punkte in 90 Tagen");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Objektorientierte_Softwareentwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Klassen]]
  - [[Methoden]]
  - [[Attribute]]
  - [[Assoziationen]]
  - [[Komponenten]]
  - [[Konnektoren]]
- **Querverweise:** keine
