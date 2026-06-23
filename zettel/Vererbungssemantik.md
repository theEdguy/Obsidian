---
id: 5db9881d-9171-4829-92a2-51095c3e5362
title: "Vererbungssemantik"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Vererbungssemantik]]

- **Kernkonzept:** Vererbungssemantik definiert die Bedeutung und Regeln der Vererbung in der objektorientierten Modellierung, insbesondere wie Unterklassen Eigenschaften und Verhalten ihrer Oberklassen übernehmen, erweitern oder einschränken. Sie legt fest, dass Instanzen von Unterklassen stets auch Instanzen ihrer Oberklassen sind (Substitutionsprinzip) und klärt die semantischen Beziehungen zwischen Klassenhierarchien in UML.
- **Nutzen & Zweck:** Vererbungssemantik löst das Problem der Mehrdeutigkeit und Inkonsistenz bei der Modellierung von Klassenhierarchien, indem sie klare Regeln für die Spezialisierung und Generalisierung von Klassen vorgibt. Sie ermöglicht eine präzise Abbildung von 'Ist-ein'-Beziehungen, sichert die Wiederverwendbarkeit von Code und Struktur und gewährleistet, dass Modelle methodisch korrekt und verständlich sind. Ohne diese Semantik wären Vererbungsstrukturen interpretationsabhängig und fehleranfällig.
- **Abgrenzung & Grenzen:** Vererbungssemantik sollte nicht genutzt werden, wenn die Beziehung zwischen Klassen keine echte Spezialisierung darstellt (z. B. bei 'Hat-ein'- oder 'Nutzt-ein'-Beziehungen), da dies zu unnatürlichen Hierarchien führt. Alternativen wie Komposition oder Interfaces sind dann vorzuziehen. Zudem ist sie ungeeignet, wenn die Unterklasse die Invarianten der Oberklasse verletzt (z. B. Quadrat-Rechteck-Problem), da dies das Substitutionsprinzip bricht. Bei Mehrfachvererbung ist Vorsicht geboten, da sie zu komplexen und schwer wartbaren Strukturen führen kann.
- **Beispiel / Code:** ```java
// Beispiel für korrekte Vererbungssemantik (Spezialisierung)
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
        super(seitenlaenge, seitenlaenge); // Erzwingt a = b
    }
    
    @Override
    public void stretch(int i, int j) {
        // Problem: Verletzung der Vererbungssemantik, da a != b möglich
        // Besser: Methode ablehnen oder Komposition nutzen
        throw new UnsupportedOperationException("Quadrat kann nicht ungleichmäßig gestreckt werden.");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:**
  - [[Spezialisierung]]
  - [[Disjoint-Vererbung]]
  - [[Overlapping-Vererbung]]
  - [[Complete-Vererbung]]
  - [[Incomplete-Vererbung]]
- **Querverweise:** keine
