---
id: fb295eed-c6c3-4f1f-bfa5-377b91e80d9c
title: "Abstrakte_Fabrik_(Abstract_Factory)"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - erzeugungsmuster
  - architektur
  - draft
source: "SWE Slides (Folien 346-360)"
---

# [[Abstrakte_Fabrik_(Abstract_Factory)]]

- **Kernkonzept:** Die [[Abstrakte_Fabrik_(Abstract_Factory)|abstrakte Fabrik]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das [[Schnittstelle|Schnittstellen]] zur Erstellung von [[Produktfamilie|Produktfamilien]] bereitstellt, ohne deren konkrete [[Klasse|Klassen]] zu spezifizieren.
- **Nutzen & Zweck:** Sie ermöglicht die Erstellung von [[Objektgruppe|Objektgruppen]], die zueinander passen, und fördert die [[Konsistenz]] innerhalb einer [[Produktfamilie]]. Durch den Austausch der [[Fabrik|Fabriken]] können ganze [[Produktfamilie|Produktfamilien]] ausgetauscht werden, z. B. für [[Internationalisierung]] oder [[Themenwechsel]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn neue [[Produkt|Produkte]] häufig hinzugefügt werden müssen, da alle [[Fabrik|Fabriken]] angepasst werden müssen. Alternativen sind [[Fabrikmethode]] oder [[Prototyp_Muster]], wenn weniger [[Kopplung]] gewünscht ist.
- **Beispiel / Code:** ```java
interface LabelFactory {
    AddressLabel mkAddressLabel();
    TelephoneLabel mkTelephoneLabel();
    BusinessLabel mkBusinessLabel();
}

class GermanLabelFactory implements LabelFactory {
    public AddressLabel mkAddressLabel() { return new GermanAddressLabel(); }
    public TelephoneLabel mkTelephoneLabel() { return new GermanTelephoneLabel(); }
    public BusinessLabel mkBusinessLabel() { return new GermanBusinessLabel(); }
}
```
