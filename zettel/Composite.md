---
id: 158db59e-9606-4798-bb02-9cddc12b34c7
title: "Composite"
date: 2026-06-23
tags:
  - software_engineering
  - composite
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Composite]]

- **Kernkonzept:** Das Composite-Muster ist ein strukturelles Design-Pattern, das es ermöglicht, Objekte zu Baumstrukturen zusammenzufassen, um Teil-Ganzes-Hierarchien darzustellen. Es behandelt einzelne Objekte und Kompositionen von Objekten einheitlich, sodass Clients nicht zwischen einfachen und zusammengesetzten Objekten unterscheiden müssen.
- **Nutzen & Zweck:** Das Composite-Muster löst das Problem, dass Clients bei der Verarbeitung von Objekthierarchien zwischen einzelnen Objekten und Gruppen von Objekten unterscheiden müssen. Es vereinfacht die Handhabung komplexer Strukturen, indem es eine einheitliche Schnittstelle für beide Fälle bereitstellt. Dadurch wird die Code-Wiederverwendung gefördert und die Flexibilität bei der Erweiterung von Hierarchien erhöht, da neue Komponenten ohne Anpassung der Client-Logik hinzugefügt werden können.
- **Abgrenzung & Grenzen:** Das Composite-Muster sollte nicht verwendet werden, wenn die Hierarchie der Objekte flach oder einfach strukturiert ist, da der Overhead der Baumverwaltung unnötig ist. Es eignet sich auch nicht, wenn die Objekte in der Hierarchie stark unterschiedliche Verantwortlichkeiten haben, da dies die einheitliche Schnittstelle aufweichen würde. Alternativen wie das Decorator-Pattern kommen infrage, wenn dynamische Erweiterungen von Objekten ohne Hierarchie im Vordergrund stehen. Zudem kann das Muster zu unübersichtlichen Strukturen führen, wenn die Hierarchie zu tief oder zu komplex wird.
- **Beispiel / Code:** ```java
// Komponente
interface Component {
    void operation();
}

// Blatt
class Leaf implements Component {
    @Override
    public void operation() {
        System.out.println("Leaf operation");
    }
}

// Composite
class Composite implements Component {
    private List<Component> children = new ArrayList<>();

    public void add(Component component) {
        children.add(component);
    }

    public void remove(Component component) {
        children.remove(component);
    }

    @Override
    public void operation() {
        System.out.println("Composite operation");
        for (Component child : children) {
            child.operation();
        }
    }
}

// Client-Code
public class Client {
    public static void main(String[] args) {
        Component leaf = new Leaf();
        Component composite = new Composite();
        ((Composite) composite).add(leaf);
        composite.operation();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7b4
- **Vorgänger / Parent:** [[Strukturmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Strukturmuster]]
  - [[Design_Pattern]]
