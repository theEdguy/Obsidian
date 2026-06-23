---
id: ca93708c-79c7-462d-8656-a856de903aab
title: "Decorator"
date: 2026-06-23
tags:
  - software_engineering
  - decorator
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Decorator]]

- **Kernkonzept:** Das Decorator-Muster ist ein strukturelles Entwurfsmuster, das es ermöglicht, Objekte dynamisch mit zusätzlichen Verantwortlichkeiten oder Funktionalitäten zu erweitern, ohne deren Klasse zu verändern oder Vererbung zu nutzen.
- **Nutzen & Zweck:** Der Decorator löst das Problem, dass statische Vererbung oft zu einer unübersichtlichen Klassenhierarchie führt, wenn viele Kombinationen von Funktionalitäten benötigt werden. Er ermöglicht eine flexible, modulare Erweiterung von Objekten zur Laufzeit, indem er Funktionalitäten in separate Decorator-Klassen kapselt, die das ursprüngliche Objekt umschließen und dessen Verhalten erweitern.
- **Abgrenzung & Grenzen:** Das Decorator-Muster sollte nicht verwendet werden, wenn die Erweiterungen statisch sind und keine dynamische Kombination erforderlich ist, da es zusätzlichen Overhead durch die Verschachtelung von Objekten erzeugt. Alternativen wie Vererbung oder Strategie-Muster sind einfacher, wenn nur eine feste Erweiterung benötigt wird. Zudem kann eine tiefe Decorator-Verschachtelung die Lesbarkeit und Wartbarkeit des Codes beeinträchtigen.
- **Beispiel / Code:** ```java
// Komponente
interface Kaffee {
    double getKosten();
    String getBeschreibung();
}

// Konkrete Komponente
class EinfacherKaffee implements Kaffee {
    @Override
    public double getKosten() {
        return 1.0;
    }
    
    @Override
    public String getBeschreibung() {
        return "Einfacher Kaffee";
    }
}

// Abstrakter Decorator
abstract class KaffeeDecorator implements Kaffee {
    protected Kaffee kaffee;
    
    public KaffeeDecorator(Kaffee kaffee) {
        this.kaffee = kaffee;
    }
    
    @Override
    public double getKosten() {
        return kaffee.getKosten();
    }
    
    @Override
    public String getBeschreibung() {
        return kaffee.getBeschreibung();
    }
}

// Konkreter Decorator
class MilchDecorator extends KaffeeDecorator {
    public MilchDecorator(Kaffee kaffee) {
        super(kaffee);
    }
    
    @Override
    public double getKosten() {
        return super.getKosten() + 0.5;
    }
    
    @Override
    public String getBeschreibung() {
        return super.getBeschreibung() + ", mit Milch";
    }
}

// Verwendung
public class Main {
    public static void main(String[] args) {
        Kaffee kaffee = new EinfacherKaffee();
        kaffee = new MilchDecorator(kaffee);
        System.out.println(kaffee.getBeschreibung() + ": " + kaffee.getKosten());
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7b2
- **Vorgänger / Parent:** [[Strukturmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Strukturmuster]]
  - [[Design_Pattern]]
