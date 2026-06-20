---
id: a4955773-3911-5c7e-b98a-9dc4581a70cc
title: "Objekt-Adapter"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_15
  - draft
source: "Kapitel 15: Patterns – Strukturmuster"
---

# [[Objekt-Adapter]]

- **Kernkonzept:** Realisiert den Adapter über Objektkomposition. Er hält eine Referenz auf den Adaptee und delegiert Aufrufe. Funktioniert auch mit Unterklassen des Adaptees.
- **Nutzen & Zweck:** Realisiert den Adapter über Objektkomposition. Er hält eine Referenz auf den Adaptee und delegiert Aufrufe. Funktioniert auch mit Unterklassen des Adaptees.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
public class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee a) { this.adaptee = a; }
    public void targetOp() { this.adaptee.existingOp(); }
}
```
