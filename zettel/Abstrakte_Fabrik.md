---
id: bf2bfa46-70fe-4a92-9177-944a70b1aa11
title: "Abstrakte_Fabrik"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - software_architecture
  - oop
  - draft
source: "SWE Slides (Folien 331-345)"
---

# [[Abstrakte_Fabrik]]

- **Kernkonzept:** Die [[Abstrakte_Fabrik]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das eine [[Schnittstelle]] zur Erzeugung von [[Familie|Familien]] verwandter oder abhängiger [[Objekt|Objekte]] bereitstellt, ohne deren konkrete [[Klasse|Klassen]] zu spezifizieren.
- **Nutzen & Zweck:** Sie löst das [[Problem]] der [[Konsistenz]] bei der Erzeugung von [[Objekt|Objekten]], die zusammengehören (z. B. [[UI-Komponente|UI-Komponenten]] für ein bestimmtes [[Look_and_Feel]]). Sie ermöglicht die [[Erstellung]] ganzer [[Produktfamilie|Produktfamilien]] ohne [[Abhängigkeit]] von deren konkreten [[Implementierung|Implementierungen]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn nur ein einzelnes [[Objekt]] erzeugt werden muss oder die [[Produktfamilie|Produktfamilien]] einfach sind. Im Vergleich zur [[Fabrikmethode]] ist sie komplexer und schwerer zu erweitern. Bei vielen [[Produkt|Produktvarianten]] kann sie zu einer [[Klassenexplosion]] führen.
- **Beispiel / Code:** ```java
interface AddressFactory {
    AddressLabel createAddressLabel();
    TelephoneLabel createTelephoneLabel();
    BusinessLabel createBusinessLabel();
}

class FrenchAddressFactory implements AddressFactory {
    public AddressLabel createAddressLabel() { return new FrenchAL(); }
    public TelephoneLabel createTelephoneLabel() { return new FrenchTL(); }
    public BusinessLabel createBusinessLabel() { return new FrenchBL(); }
}
```
