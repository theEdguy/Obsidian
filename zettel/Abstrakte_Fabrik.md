---
id: f38f3d52-4c0a-4219-a1df-6dd931dc95e9
title: "Abstrakte_Fabrik"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - software_architecture
  - oop
  - erzeugung
  - fabrik
  - draft
source: "software_engineering_kapitel_14"
---

# [[Abstrakte_Fabrik]]

- **Kernkonzept:** Die [[Abstrakte_Fabrik]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]] in der [[objektorientierten_Programmierung|objektorientierten Programmierung]], das eine [[Schnittstelle]] zur Erzeugung von [[Familie|Familien]] verwandter oder abhängiger [[Objekt|Objekte]] bereitstellt, ohne deren konkrete [[Klasse|Klassen]] zu spezifizieren. Sie kapselt die [[Objekterzeugung]] und garantiert die [[Konsistenz]] der erzeugten [[Objekt|Objekte]] untereinander.
- **Nutzen & Zweck:** Dieses [[Entwurfsmuster|Muster]] löst das [[Problem]], wenn ein [[System]] unabhängig von der Art und Weise sein soll, wie seine [[Objekt|Objekte]] erzeugt, zusammengesetzt und repräsentiert werden. Es ermöglicht die Erstellung konsistenter [[Produktfamilie|Produktfamilien]], die aufeinander abgestimmt sind, und erleichtert den Austausch ganzer [[Produktfamilie|Produktfamilien]] ohne Änderungen am bestehenden [[Code]]. Besonders nützlich ist es in internationalen [[Anwendung|Anwendungen]], wo länderspezifische Varianten von [[Objekt|Objekten]] (z. B. [[Adressformat|Adressformate]]) benötigt werden, oder in [[Framework|Frameworks]], die [[Erweiterbarkeit]] durch [[Plug-in|Plug-ins]] unterstützen sollen. Die [[Abstrakte_Fabrik]] fördert zudem [[Lose_Kopplung|lose Kopplung]] und [[Modularität]] im [[Softwareentwurf]].
- **Abgrenzung & Grenzen:** Die [[Abstrakte_Fabrik]] sollte nicht eingesetzt werden, wenn die zu erzeugenden [[Objekt|Objekte]] keine logische [[Familie]] bilden oder keine [[Abhängigkeit|Abhängigkeiten]] untereinander aufweisen, da der [[Overhead]] der [[Musterimplementierung]] dann unnötig ist. Im Vergleich zur [[Fabrikmethode]], die sich auf die Erzeugung eines einzelnen [[Objekt|Objekts]] konzentriert, ist die [[Abstrakte_Fabrik]] komplexer und weniger flexibel bei der Erweiterung um neue [[Produkt|Produkttypen]], da alle konkreten [[Fabrik|Fabriken]] angepasst werden müssen. Bei einfachen [[Erzeugungsproblem|Erzeugungsproblemen]] reichen oft einfachere [[Entwurfsmuster|Muster]] wie der [[Builder]] oder direkte [[Instanziierung]] aus. Zudem kann die starre Kopplung an [[Produktfamilie|Produktfamilien]] die [[Wartbarkeit]] erschweren, wenn sich [[Anforderung|Anforderungen]] häufig ändern. Eine [[Klassenexplosion]] ist möglich, wenn viele [[Produktvariante|Produktvarianten]] unterstützt werden müssen.
- **Beispiel / Code:** ```java
// Abstrakte Fabrik-Schnittstelle
interface LabelFactory {
    AddressLabel createAddressLabel();
    TelephoneLabel createTelephoneLabel();
    BusinessLabel createBusinessLabel();
}

// Konkrete Fabrik für französische Adressen
class FrenchLabelFactory implements LabelFactory {
    public AddressLabel createAddressLabel() {
        return new FrenchAddressLabel();
    }
    public TelephoneLabel createTelephoneLabel() {
        return new FrenchTelephoneLabel();
    }
    public BusinessLabel createBusinessLabel() {
        return new FrenchBusinessLabel();
    }
}

// Konkrete Fabrik für deutsche Adressen
class GermanLabelFactory implements LabelFactory {
    public AddressLabel createAddressLabel() {
        return new GermanAddressLabel();
    }
    public TelephoneLabel createTelephoneLabel() {
        return new GermanTelephoneLabel();
    }
    public BusinessLabel createBusinessLabel() {
        return new GermanBusinessLabel();
    }
}

// Verwendung im Adressbuch
class AddressBook {
    private LabelFactory factory;
    
    public AddressBook(LabelFactory factory) {
        this.factory = factory;
    }
    
    public BusinessCard createBusinessCard() {
        BusinessCard card = new BusinessCard();
        card.addAddressLabel(factory.createAddressLabel());
        card.addTelephoneLabel(factory.createTelephoneLabel());
        card.addBusinessLabel(factory.createBusinessLabel());
        return card;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1b
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:**
  - [[Zweck_der_abstrakten_Fabrik]]
  - [[Anwendbarkeit_der_abstrakten_Fabrik]]
  - [[Konsequenzen_der_abstrakten_Fabrik]]
  - [[Beispiel_LabelFactory]]
- **Querverweise:**
  - [[Fabrikmethode]]
  - [[Produktfamilien]]
