---
id: d17bd59b-46cb-4531-be36-27a5fab4f8a7
title: "Brücke_(Bridge)"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - strukturmuster
  - architektur
  - draft
source: "SWE Slides (Folien 346-360)"
---

# [[Brücke_(Bridge)]]

- **Kernkonzept:** Die [[Brücke_(Bridge)|Brücke]] ist ein [[Strukturmuster]], das die [[Abstraktion]] von ihrer [[Implementierung]] entkoppelt, sodass beide unabhängig voneinander variiert werden können.
- **Nutzen & Zweck:** Sie ermöglicht die Trennung von [[Schnittstelle]] und [[Implementierung]], was die [[Erweiterbarkeit]] und [[Wartbarkeit]] von [[Code]] verbessert. Besonders nützlich, wenn sowohl die [[Abstraktion]] als auch die [[Implementierung]] häufig geändert oder erweitert werden müssen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Abstraktion]] und [[Implementierung]] eng miteinander verbunden sind und keine unabhängige Variation erforderlich ist. Alternativen sind [[Adapter]] oder [[Strategie_Muster]], wenn nur eine [[Implementierung]] ausgetauscht werden soll.
- **Beispiel / Code:** ```java
abstract class Abstraction {
    protected Implementor impl;
    
    public Abstraction(Implementor impl) {
        this.impl = impl;
    }
    
    public abstract void operation();
}

class RefinedAbstraction extends Abstraction {
    public void operation() {
        impl.operationImpl();
    }
}
```
