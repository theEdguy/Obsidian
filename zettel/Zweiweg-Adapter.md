---
id: 27b2fddf-408f-4c3c-9f34-c93649c7fa9a
title: "Zweiweg-Adapter"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - adapter
  - schnittstellen
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Zweiweg-Adapter]]

- **Kernkonzept:** Eine erweiterte Form des [[Adapter_Pattern|Adapter-Musters]], die beide [[Schnittstelle|Schnittstellen]] (die des Clients und die des Adaptees) gleichzeitig anbietet, um die Transparenz zu erhöhen.
- **Nutzen & Zweck:** Ermöglicht die Nutzung einer [[Klasse]] sowohl über die ursprüngliche als auch über die angepasste [[Schnittstelle]]. Nützlich, wenn beide [[Schnittstelle|Schnittstellen]] parallel unterstützt werden sollen.
- **Abgrenzung & Grenzen:** Komplexer in der Implementierung und Wartung. Nicht geeignet, wenn nur eine [[Schnittstelle]] benötigt wird oder wenn die [[Schnittstelle|Schnittstellen]] stark voneinander abweichen.
- **Beispiel / Code:** ```java
// Zweiweg-Adapter
interface X {
    void xOp();
}

interface Y {
    void yOp();
}

class TwoWayAdapter implements X, Y {
    private X x;
    private Y y;
    
    TwoWayAdapter(X x, Y y) {
        this.x = x;
        this.y = y;
    }
    
    void xOp() {
        y.yOp();
    }
    
    void yOp() {
        x.xOp();
    }
}
```
