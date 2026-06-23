---
id: 7bf112b3-de15-4118-bd72-e816f6ff91b0
title: "Produktfamilien"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - fabrik
  - produktfamilie
  - draft
source: "software_engineering_kapitel_14"
---

# [[Produktfamilien]]

- **Kernkonzept:** Produktfamilien bezeichnen eine Gruppe von verwandten oder abhängigen Objekten, die gemeinsam entworfen und implementiert werden, um eine konsistente und aufeinander abgestimmte Funktionalität zu gewährleisten. Sie werden typischerweise durch das Abstrakte-Fabrik-Muster realisiert, das die Erzeugung dieser Objekte zentralisiert und koordiniert.
- **Nutzen & Zweck:** Das Konzept der Produktfamilien löst das Problem inkonsistenter oder inkompatibler Objektkombinationen, die entstehen, wenn verwandte Objekte unabhängig voneinander erzeugt werden. Es stellt sicher, dass nur kompatible Objekte miteinander interagieren, indem es deren Erzeugung über eine zentrale Fabrik steuert. Dies erhöht die Wartbarkeit, reduziert Fehler durch falsche Kombinationen und ermöglicht eine einfache Erweiterung um neue Varianten, ohne bestehenden Code zu modifizieren.
- **Abgrenzung & Grenzen:** Produktfamilien sollten nicht genutzt werden, wenn die zu erzeugenden Objekte keine logische oder funktionale Abhängigkeit zueinander haben oder wenn die Anzahl der Produktvarianten sehr dynamisch oder unvorhersehbar ist. Im Vergleich zur Fabrikmethode, die sich auf die Erzeugung einzelner Objekte konzentriert, ist das Abstrakte-Fabrik-Muster komplexer und weniger flexibel bei der Erweiterung um neue Produkttypen. Bei einfachen Szenarien mit wenigen Objektvarianten kann eine direkte Instanziierung oder eine parametrisierte Fabrikmethode effizienter sein.
- **Beispiel / Code:** ```java
// Abstrakte Fabrik für eine Produktfamilie (z. B. internationale Adresslabels)
interface LabelFactory {
    AddressLabel createAddressLabel();
    TelephoneLabel createTelephoneLabel();
    BusinessLabel createBusinessLabel();
}

// Konkrete Fabrik für deutsche Adresslabels
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

// Verwendung der Fabrik im Adressbuch
class AddressBook {
    private LabelFactory labelFactory;
    
    public AddressBook(LabelFactory factory) {
        this.labelFactory = factory;
    }
    
    public BusinessCard createBusinessCard() {
        BusinessCard card = new BusinessCard();
        card.addAddressLabel(labelFactory.createAddressLabel());
        card.addTelephoneLabel(labelFactory.createTelephoneLabel());
        card.addBusinessLabel(labelFactory.createBusinessLabel());
        return card;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1b1
- **Vorgänger / Parent:** [[Abstrakte_Fabrik]]
- **Folgezettel / Unterzettel:**
  - [[Unterstützung_durch_abstrakte_Fabriken]]
  - [[Beispiel_LabelFactory]]
- **Querverweise:**
  - [[Fabrikmethode]]
  - [[Erzeugungsmuster]]
