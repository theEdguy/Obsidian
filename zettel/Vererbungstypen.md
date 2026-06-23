---
id: 1c03a70b-4b49-48da-babb-2ff7169a096b
title: "Vererbungstypen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - typen
  - draft
source: "software_engineering_kapitel_04"
---

# [[Vererbungstypen]]

- **Kernkonzept:** Vererbungstypen klassifizieren die Art und Weise, wie Klassen in der objektorientierten Programmierung hierarchisch voneinander abgeleitet werden, insbesondere hinsichtlich der Semantik und der Beziehungen zwischen Ober- und Unterklassen. Sie definieren, ob eine Spezialisierung, Generalisierung oder eine andere Form der Vererbung vorliegt und wie Instanzen der Unterklassen im Verhältnis zur Oberklasse stehen.
- **Nutzen & Zweck:** Vererbungstypen ermöglichen eine präzise Modellierung von Klassenhierarchien, indem sie klare Regeln für die Beziehung zwischen Ober- und Unterklassen festlegen. Sie lösen das Problem der Mehrdeutigkeit bei der Vererbung, indem sie sicherstellen, dass Unterklassen die Eigenschaften und Methoden der Oberklasse korrekt erweitern oder einschränken. Dadurch wird die Wiederverwendbarkeit von Code gefördert und die Konsistenz im Design gewährleistet, insbesondere in komplexen Systemen mit vielen Klassen und Beziehungen.
- **Abgrenzung & Grenzen:** Vererbungstypen sollten nicht genutzt werden, wenn die Beziehung zwischen Klassen keine echte „Ist-ein“-Beziehung darstellt, wie im Beispiel von Rechteck und Quadrat, wo Vererbung zu semantischen Widersprüchen führen kann. Alternativen wie Komposition oder das Hinzufügen von Methoden zur Überprüfung von Eigenschaften (z. B. `istQuadrat()`) sind oft sinnvoller. Zudem sind Vererbungstypen wie `overlapping` oder `disjoint` nur relevant, wenn Mehrfachvererbung oder spezifische Mengeneinschränkungen modelliert werden müssen. Bei einfachen Hierarchien können sie unnötige Komplexität einführen.
- **Beispiel / Code:** ```java
// Beispiel für Spezialisierung (Ist-ein-Vererbung)
class Mitglied {
    protected String name;
    
    public Mitglied(String name) {
        this.name = name;
    }
}

// Unterklasse mit erweiterter Funktionalität
class Vorstandsmitglied extends Mitglied {
    private String rolle;
    
    public Vorstandsmitglied(String name, String rolle) {
        super(name);
        this.rolle = rolle;
    }
}

// Beispiel für eine problematische Vererbung (Rechteck/Quadrat)
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

// Quadrat als Unterklasse von Rechteck führt zu Problemen
class Quadrat extends Rechteck {
    public Quadrat(int seite) {
        super(seite, seite);
    }
    
    @Override
    public void stretch(int i, int j) {
        // Verletzung der Quadrat-Eigenschaft (a = b)
        super.stretch(i, j);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Einfachvererbung]]
  - [[Mehrfachvererbung]]
