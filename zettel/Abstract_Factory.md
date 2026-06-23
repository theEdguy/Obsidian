---
id: cea3aaf1-f49c-4d0e-a129-6ac8087355d0
title: "Abstract Factory"
date: 2026-06-23
tags:
  - software_engineering
  - abstract_factory
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Abstract Factory]]

- **Kernkonzept:** Die Abstract Factory ist ein Entwurfsmuster, das eine Schnittstelle zum Erstellen von Familien verwandter oder abhängiger Objekte bereitstellt, ohne deren konkrete Klassen zu spezifizieren.
- **Nutzen & Zweck:** Dieses Muster löst das Problem, wenn ein System unabhängig von der Art und Weise sein soll, wie seine Objekte erstellt werden. Es ermöglicht die Kapselung der Objekterzeugung und fördert die Konsistenz zwischen den erzeugten Objekten, indem sichergestellt wird, dass diese zueinander passen. Besonders nützlich ist es in Systemen, die mit mehreren Produktvarianten umgehen müssen, ohne den Code bei Erweiterungen stark anpassen zu müssen.
- **Abgrenzung & Grenzen:** Die Abstract Factory sollte nicht verwendet werden, wenn das System nur eine einzige Produktfamilie benötigt oder wenn die Objekterzeugung einfach und nicht variabel ist. Im Vergleich zum Factory Method Pattern, das sich auf die Erstellung eines einzelnen Objekts konzentriert, ist die Abstract Factory komplexer und schwerer zu erweitern, da sie ganze Objektfamilien verwaltet. Sie ist auch weniger geeignet, wenn die Produktfamilien häufig wechseln oder wenn die Anzahl der zu erstellenden Objekte dynamisch variiert.
- **Beispiel / Code:** ```java
// Schnittstelle für die Abstract Factory
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}

// Konkrete Factory für Windows
class WindowsFactory implements GUIFactory {
    public Button createButton() {
        return new WindowsButton();
    }
    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

// Konkrete Factory für macOS
class MacOSFactory implements GUIFactory {
    public Button createButton() {
        return new MacOSButton();
    }
    public Checkbox createCheckbox() {
        return new MacOSCheckbox();
    }
}

// Schnittstelle für Produkte
interface Button {
    void paint();
}

// Konkrete Produkte
class WindowsButton implements Button {
    public void paint() {
        System.out.println("Windows Button gerendert.");
    }
}

class MacOSButton implements Button {
    public void paint() {
        System.out.println("macOS Button gerendert.");
    }
}

// Verwendung
public class Application {
    private GUIFactory factory;
    
    public Application(GUIFactory factory) {
        this.factory = factory;
    }
    
    public void createUI() {
        Button button = factory.createButton();
        button.paint();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7a3
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Erzeugungsmuster]]
  - [[Design_Pattern]]
