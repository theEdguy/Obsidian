---
id: 443429b8-3832-4491-8302-601bee8af65c
title: "Taxonomie"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - klassifikation
  - draft
source: "software_engineering_kapitel_03"
---

# [[Taxonomie]]

- **Kernkonzept:** Taxonomie bezeichnet in der objektorientierten Modellierung die systematische Zusammenfassung gleichartiger Objekte zu Klassen, um deren Struktur und Verhalten einheitlich zu beschreiben. Sie ermöglicht die hierarchische Ordnung von Konzepten nach Gemeinsamkeiten und Unterschieden.
- **Nutzen & Zweck:** Taxonomie löst das Problem der Komplexitätsreduktion, indem sie reale oder abstrakte Entitäten nach gemeinsamen Merkmalen gruppiert. Dadurch wird die Wiederverwendung von Code und Modellen gefördert, die Kommunikation zwischen Entwicklern und Domänenexperten vereinfacht und die Konsistenz von Software-Systemen verbessert. Sie schafft eine gemeinsame Sprache für die Beschreibung von Problem- und Lösungsräumen.
- **Abgrenzung & Grenzen:** Taxonomie sollte nicht genutzt werden, wenn Objekte keine gemeinsamen Eigenschaften oder Verhaltensweisen aufweisen, da dies zu künstlichen oder übermäßig abstrakten Hierarchien führt. Alternativen wie Komposition oder lose Kopplung über Interfaces sind vorzuziehen, wenn Objekte zwar ähnliche Schnittstellen, aber stark unterschiedliche Implementierungen benötigen. Zudem ist Taxonomie ungeeignet für dynamische Systeme, in denen sich Objektmerkmale zur Laufzeit grundlegend ändern.
- **Beispiel / Code:** ```java
// Beispiel einer taxonomischen Hierarchie in Java
abstract class Sportler {
    private String name;
    private int alter;
    
    public Sportler(String name, int alter) {
        this.name = name;
        this.alter = alter;
    }
    
    public abstract double berechneLeistung();
}

class Bogenschuetze extends Sportler {
    private int trefferquote;
    
    public Bogenschuetze(String name, int alter, int trefferquote) {
        super(name, alter);
        this.trefferquote = trefferquote;
    }
    
    @Override
    public double berechneLeistung() {
        return trefferquote * 0.8;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
