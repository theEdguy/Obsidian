---
id: 241917be-d30e-4c65-8b05-55f62df75158
title: "Prototyp_Muster"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - erzeugungsmuster
  - draft
source: "SWE Slides (Folien 346-360)"
---

# [[Prototyp_Muster]]

- **Kernkonzept:** Das [[Prototyp_Muster]] ist ein [[Erzeugungsmuster]], das die Erstellung neuer [[Objekt|Objekte]] durch das Klonen eines bestehenden [[Prototyp|Prototyps]] ermöglicht.
- **Nutzen & Zweck:** Es reduziert die Notwendigkeit, [[Klasse|Klassen]] für die Erstellung von [[Objekt|Objekten]] zu instanziieren, und ist besonders nützlich, wenn die Erstellung eines [[Objekt|Objekts]] teuer oder komplex ist. Es fördert die [[Flexibilität]] bei der [[Objekterstellung]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Objekt|Objekte]] viele interne [[Zustand|Zustände]] haben, die nicht einfach kopiert werden können. Alternativen sind [[Abstrakte_Fabrik_(Abstract_Factory)|abstrakte Fabriken]] oder [[Fabrikmethode]], wenn die [[Kopplung]] zu konkreten [[Klasse|Klassen]] vermieden werden soll.
- **Beispiel / Code:** ```java
class LabelFactory {
    private AddressLabel addressLabelPrototype;
    
    public AddressLabel newAddressLabel() {
        return addressLabelPrototype.clone();
    }
}
```
