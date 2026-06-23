---
id: f5aa33a5-af6e-40e7-a029-7df304d03dac
title: "Einfachvererbung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - typen
  - draft
source: "software_engineering_kapitel_04"
---

# [[Einfachvererbung]]

- **Kernkonzept:** Einfachvererbung ist ein grundlegendes Prinzip der objektorientierten Programmierung, bei dem eine Klasse (Unterklasse) alle Eigenschaften und Methoden einer anderen Klasse (Oberklasse) übernimmt, diese erweitern oder überschreiben kann, jedoch keine Eigenschaften eliminiert. Sie ermöglicht eine hierarchische Strukturierung von Klassen nach dem 'Ist-ein'-Prinzip (Substitutionsprinzip).
- **Nutzen & Zweck:** Einfachvererbung existiert, um Code-Wiederverwendung und Modularität in der Softwareentwicklung zu fördern. Sie löst das Problem redundanter Implementierungen, indem gemeinsame Attribute und Methoden in einer Oberklasse zentralisiert werden. Dadurch wird die Wartbarkeit verbessert, da Änderungen nur an einer Stelle vorgenommen werden müssen. Zudem ermöglicht sie Polymorphismus, bei dem Objekte der Unterklasse als Instanzen der Oberklasse behandelt werden können, was flexible und erweiterbare Systeme unterstützt.
- **Abgrenzung & Grenzen:** Einfachvererbung sollte nicht genutzt werden, wenn die Beziehung zwischen den Klassen keine klare 'Ist-ein'-Hierarchie darstellt, da dies zu unnatürlichen oder schwer verständlichen Modellen führt. Sie ist ungeeignet, wenn eine Klasse Eigenschaften mehrerer Oberklassen benötigt (Mehrfachvererbung), da dies in vielen Sprachen nicht unterstützt wird. Alternativen wie Komposition oder Interfaces sind vorzuziehen, wenn die Beziehung eher 'Hat-ein' oder 'Kann-etwas' beschreibt. Zudem kann Einfachvererbung zu Problemen wie dem 'fragilen Basisklassenproblem' führen, bei dem Änderungen an der Oberklasse unerwartete Auswirkungen auf Unterklassen haben.
- **Beispiel / Code:** ```java
// Oberklasse
class Rechteck {
    protected int a;
    protected int b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public int flaeche() {
        return a * b;
    }
}

// Unterklasse (erbt von Rechteck)
class Quadrat extends Rechteck {
    public Quadrat(int seitenlaenge) {
        super(seitenlaenge, seitenlaenge); // Aufruf des Oberklassen-Konstruktors
    }
    
    // Überschreiben der flaeche()-Methode (optional)
    @Override
    public int flaeche() {
        return a * a; // Spezifische Implementierung für Quadrate
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1
- **Vorgänger / Parent:** [[Vererbungstypen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
