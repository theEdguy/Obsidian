---
id: f3414742-6e4e-4d60-a015-cdf621fb9dab
title: "Vererbungsbeispiel"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - beispiel
  - draft
source: "software_engineering_kapitel_04"
---

# [[Vererbungsbeispiel]]

- **Kernkonzept:** Das Vererbungsbeispiel im Kontext der Objektorientierung illustriert, wie eine Unterklasse (z. B. Quadrat) die Eigenschaften und Methoden einer Oberklasse (z. B. Rechteck) erbt, diese erweitern oder überschreiben kann, jedoch die grundlegende Struktur und Semantik der Oberklasse beibehalten muss. Es zeigt die Anwendung des Substitutionsprinzips, wonach Objekte der Unterklasse als Objekte der Oberklasse behandelt werden können.
- **Nutzen & Zweck:** Dieses Konzept dient dazu, die Wiederverwendung von Code und die Modellierung hierarchischer Beziehungen zwischen Klassen zu ermöglichen. Es löst das Problem der Redundanz, indem gemeinsame Attribute und Methoden in einer Oberklasse zentralisiert werden. Gleichzeitig ermöglicht es die Spezialisierung von Klassen, um domänenspezifische Anforderungen abzubilden, ohne die bestehende Logik neu implementieren zu müssen.
- **Abgrenzung & Grenzen:** Vererbung sollte nicht genutzt werden, wenn die Beziehung zwischen den Klassen keine echte „Ist-ein“-Beziehung darstellt oder wenn die Unterklasse die Semantik der Oberklasse verletzt (z. B. Quadrat als Unterklasse von Rechteck, wenn die Methode `stretch` die quadratische Form zerstört). Alternativen wie Komposition oder das Hinzufügen von Methoden zur Überprüfung (z. B. `istQuadrat()`) sind oft sinnvoller, wenn die Vererbungshierarchie zu unflexibel oder fehleranfällig wird. Zudem sollte Vererbung vermieden werden, wenn die Klassen keine gemeinsame Schnittstelle oder logische Hierarchie teilen.
- **Beispiel / Code:** ```java
// Oberklasse
class Rechteck {
    protected int a;
    protected int b;

    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }

    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
}

// Unterklasse (problematisch)
class Quadrat extends Rechteck {
    public Quadrat(int seitenlaenge) {
        super(seitenlaenge, seitenlaenge);
    }

    @Override
    public void stretch(int i, int j) {
        // Verletzung der Quadrat-Semantik, wenn i != j
        super.stretch(i, j);
    }
}

// Alternative ohne Vererbung
class RechteckAlternative {
    private int a;
    private int b;

    public RechteckAlternative(int a, int b) {
        this.a = a;
        this.b = b;
    }

    public boolean istQuadrat() {
        return a == b;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:**
  - [[Quadrat-Rechteck-Problem]]
  - [[Vererbungssicherheit]]
- **Querverweise:** keine
