---
id: 92a7543b-9aa1-48f4-9946-e42bc8562602
title: "Objekt-Adapter"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - komposition
  - adapter
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Objekt-Adapter]]

- **Kernkonzept:** Eine Variante des [[Adapter_Pattern|Adapter-Musters]], bei der der Adapter eine [[Instanz]] der zu adaptierenden [[Klasse]] (Adaptee) als [[Attribut]] hält und die [[Schnittstelle]] des Clients durch [[Komposition]] anpasst.
- **Nutzen & Zweck:** Ermöglicht die Zusammenarbeit mit mehreren [[Unterklasse|Unterklassen]] des Adaptees und bietet mehr Flexibilität als der [[Klassen-Adapter]]. Geeignet, wenn das Verhalten des Adaptees durch [[Unterklasse|Unterklassen]] verändert werden soll.
- **Abgrenzung & Grenzen:** Komplexer als der [[Klassen-Adapter]], da er [[Komposition]] statt [[Vererbung]] nutzt. Nicht geeignet, wenn die [[Schnittstelle]] des Adaptees nicht durch [[Unterklasse|Unterklassen]] erweitert werden kann.
- **Beispiel / Code:** ```java
// Objekt-Adapter
class ObjectAdapter implements Target {
    private Adaptee adaptee;
    
    ObjectAdapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    
    void targetOp() {
        adaptee.existingOp();
    }
}
```
