---
id: c8ce9fba-3646-405f-b85a-34ab03379102
title: "Assoziationsklasse"
date: 2026-06-23
tags:
  - software_engineering
  - klassendiagramm
  - beziehung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Assoziationsklasse]]

- **Kernkonzept:** Eine Assoziationsklasse ist eine spezielle Klasse in der UML, die Eigenschaften und Verhalten einer Assoziation zwischen zwei oder mehr Klassen kapselt. Sie verbindet die Eigenschaften einer Klasse mit denen einer Assoziation, um Attribute oder Operationen zu modellieren, die direkt zur Beziehung selbst gehören und nicht einer der beteiligten Klassen zugeordnet werden können.
- **Nutzen & Zweck:** Die Assoziationsklasse löst das Problem, dass bestimmte Eigenschaften oder Operationen nicht eindeutig einer der an einer Beziehung beteiligten Klassen zugeordnet werden können, sondern direkt zur Beziehung selbst gehören. Sie ermöglicht es, Metadaten oder zusätzliche Informationen zu einer Assoziation zu speichern, wie z. B. den Zeitpunkt, zu dem eine Beziehung hergestellt wurde, oder weitere beschreibende Attribute. Dadurch wird die Modellierung präziser und die Semantik der Beziehung klarer dargestellt.
- **Abgrenzung & Grenzen:** Eine Assoziationsklasse sollte nicht verwendet werden, wenn die zu modellierenden Eigenschaften oder Operationen eindeutig einer der beteiligten Klassen zugeordnet werden können. In solchen Fällen reicht eine einfache Assoziation mit Attributen in den beteiligten Klassen aus. Zudem ist sie ungeeignet, wenn die Beziehung keine zusätzlichen Attribute oder Methoden benötigt, da dies die Komplexität des Modells unnötig erhöht. Alternativen wie die Verwendung von Zwischentabellen in relationalen Datenbanken oder die Modellierung als eigenständige Klasse mit bidirektionalen Assoziationen können in manchen Fällen einfacher sein, bieten jedoch weniger semantische Klarheit für die Beziehung selbst.
- **Beispiel / Code:** ```java
// Beispiel: Assoziationsklasse 'Mitgliedschaft' zwischen 'Mitglied' und 'Verein'
class Mitglied {
    private String name;
    // Weitere Attribute und Methoden
}

class Verein {
    private String vereinsname;
    // Weitere Attribute und Methoden
}

// Assoziationsklasse
class Mitgliedschaft {
    private Mitglied mitglied;
    private Verein verein;
    private LocalDate beitrittsdatum;
    private String rolle;
    
    public Mitgliedschaft(Mitglied mitglied, Verein verein, LocalDate beitrittsdatum, String rolle) {
        this.mitglied = mitglied;
        this.verein = verein;
        this.beitrittsdatum = beitrittsdatum;
        this.rolle = rolle;
    }
    
    // Getter und Setter
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1d
- **Vorgänger / Parent:** [[Assoziation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Assoziation]]
  - [[Klassendiagramm]]
