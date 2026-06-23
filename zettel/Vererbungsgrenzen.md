---
id: 80df01dc-e0d8-424f-8dea-717a54edb289
title: "Vererbungsgrenzen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - design
  - draft
source: "software_engineering_kapitel_04"
---

# [[Vererbungsgrenzen]]

- **Kernkonzept:** Vererbungsgrenzen beschreiben die inhärenten Einschränkungen und Probleme der objektorientierten Vererbung, insbesondere wenn eine Unterklasse die Semantik oder Invarianten ihrer Oberklasse verletzt, wie im Beispiel der 'Ist-ein'-Beziehung zwischen Quadrat und Rechteck.
- **Nutzen & Zweck:** Das Konzept dient dazu, Entwickler für die Risiken und Fallstricke der Vererbung zu sensibilisieren. Es zeigt auf, wann Vererbung zu ungewollten Seiteneffekten, Verletzungen von Klasseninvarianten oder unklaren Hierarchien führt. Dadurch wird die Entscheidung unterstützt, wann Vererbung sinnvoll ist und wann Alternativen wie Komposition oder Schnittstellen bevorzugt werden sollten.
- **Abgrenzung & Grenzen:** Vererbung sollte nicht genutzt werden, wenn die Unterklasse die Invarianten oder das Verhalten der Oberklasse nicht vollständig respektiert oder wenn die 'Ist-ein'-Beziehung semantisch nicht korrekt ist. Alternativen wie Komposition (z. B. ein Rechteck enthält ein Quadrat-Objekt) oder Schnittstellen (z. B. ein gemeinsames Interface für geometrische Formen) sind oft besser geeignet, um Flexibilität und Wartbarkeit zu gewährleisten. Vererbung ist zudem ungeeignet, wenn die Hierarchie zu starr ist oder Mehrfachvererbung erforderlich wäre, die in vielen Sprachen nicht unterstützt wird.
- **Beispiel / Code:** ```java
// Problem: Quadrat erbt von Rechteck und verletzt die Invarianten der Oberklasse
class Rechteck {
    protected int a, b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
}

class Quadrat extends Rechteck {
    public Quadrat(int seitenlaenge) {
        super(seitenlaenge, seitenlaenge);
    }
    
    @Override
    public void stretch(int i, int j) {
        // Verletzung der Rechteck-Invariante: a und b müssen unabhängig sein
        super.stretch(i, i); // Erzwingt a == b, was für Rechtecke nicht gilt
    }
}

// Lösung: Komposition statt Vererbung
class RechteckKomposition {
    private int a, b;
    
    public RechteckKomposition(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public boolean istQuadrat() {
        return a == b;
    }
    
    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:**
  - [[Template-Vererbung]]
- **Querverweise:** keine
