---
id: baf085bb-ed0a-4838-80bc-a7035e50a605
title: "Factory Method"
date: 2026-06-23
tags:
  - software_engineering
  - factory_method
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Factory Method]]

- **Kernkonzept:** Die Factory Method ist ein Entwurfsmuster, das eine Schnittstelle zur Erzeugung von Objekten definiert, jedoch die konkrete Klasse der zu erzeugenden Objekte den Unterklassen überlässt. Dadurch wird die Instanziierung von Objekten flexibel und erweiterbar gestaltet.
- **Nutzen & Zweck:** Die Factory Method löst das Problem, dass Code oft direkt von konkreten Klassen abhängig ist, was Änderungen und Erweiterungen erschwert. Sie ermöglicht es, die Objekterzeugung zu zentralisieren und die Verantwortung für die Auswahl der zu instanziierenden Klasse an Unterklassen zu delegieren. Dies fördert lose Kopplung und erleichtert die Wartbarkeit sowie die Erweiterbarkeit von Software, insbesondere wenn zukünftig neue Klassen hinzugefügt werden sollen.
- **Abgrenzung & Grenzen:** Die Factory Method sollte nicht genutzt werden, wenn die Objekterzeugung einfach und unveränderlich ist, da der zusätzliche Abstraktionsaufwand dann unnötig ist. Im Vergleich zum Abstract Factory Pattern, das ganze Familien von verwandten Objekten erzeugt, ist die Factory Method auf die Erzeugung eines einzelnen Objekts beschränkt. Zudem kann sie zu einer erhöhten Anzahl von Klassen führen, was die Komplexität des Systems unnötig steigern kann, wenn keine Erweiterbarkeit benötigt wird.
- **Beispiel / Code:** ```java
// Schnittstelle für das zu erzeugende Produkt
interface Produkt {
    void operation();
}

// Konkrete Implementierung des Produkts
class KonkretesProdukt implements Produkt {
    public void operation() {
        System.out.println("Operation des konkreten Produkts");
    }
}

// Abstrakte Creator-Klasse mit der Factory Method
abstract class Creator {
    public abstract Produkt factoryMethod();

    public void anOperation() {
        Produkt produkt = factoryMethod();
        produkt.operation();
    }
}

// Konkrete Creator-Klasse, die die Factory Method implementiert
class KonkreterCreator extends Creator {
    public Produkt factoryMethod() {
        return new KonkretesProdukt();
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        Creator creator = new KonkreterCreator();
        creator.anOperation();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7a2
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Erzeugungsmuster]]
  - [[Design_Pattern]]
