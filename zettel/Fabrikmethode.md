---
id: b5524e49-9c6f-44a8-9215-bb3f4d3215fb
title: "Fabrikmethode"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - software_architecture
  - oop
  - erzeugungsmuster
  - draft
source: "SWE Slides (Folien 346-360)"
---

# [[Fabrikmethode]]

- **Kernkonzept:** Die [[Fabrikmethode]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das eine [[Schnittstelle]] zur [[Erstellung]] von [[Objekt|Objekten]] definiert, aber die konkrete [[Klasse]] der zu erzeugenden [[Objekt|Objekte]] an [[Unterklasse|Unterklassen]] delegiert. Sie ermöglicht die [[Entkopplung]] von [[Client-Code]] und konkreten [[Klasse|Klassen]], indem die [[Erstellung]] in [[Unterklasse|Unterklassen]] verlagert wird.
- **Nutzen & Zweck:** Die [[Fabrikmethode]] löst das [[Problem]] der starren [[Abhängigkeit]] von konkreten [[Klasse|Klassen]] im [[Client-Code]] und fördert die [[Erweiterbarkeit]] sowie [[Wiederverwendbarkeit]] von [[Code]]. Durch die Verlagerung der [[Objekterzeugung]] in [[Unterklasse|Unterklassen]] wird die [[Kopplung]] reduziert und die [[Flexibilität]] im [[Design]] erhöht. Dies ist besonders nützlich, wenn die genaue [[Klasse]] der zu erzeugenden [[Objekt|Objekte]] erst zur [[Laufzeit]] bestimmt werden kann oder wenn [[Erweiterungen]] ohne Änderung des bestehenden [[Code]]s möglich sein sollen.
- **Abgrenzung & Grenzen:** Die [[Fabrikmethode]] ist nicht geeignet, wenn die [[Objekterzeugung]] einfach ist oder keine [[Variabilität]] benötigt wird. Im Vergleich zur [[Abstrakte_Fabrik_(Abstract_Factory)|abstrakten Fabrik]] unterstützt sie nur die Erstellung eines einzelnen [[Produkt|Produkts]], nicht einer ganzen [[Produktfamilie]]. Sie ist daher weniger komplex, aber auch weniger mächtig, wenn mehrere [[Objekt|Objekte]] gleichzeitig erstellt und aufeinander abgestimmt werden müssen. Im Gegensatz zur [[Template_Methode]] liegt der Fokus hier auf der [[Erstellung]] von [[Objekt|Objekten]] und nicht auf der Definition eines [[Algorithmus|Algorithmusgerüsts]].
- **Beispiel / Code:** ```java
// Beispiel 1: Grundlegende Fabrikmethode
abstract class AddressBook {
    protected abstract AddressLabel mkAL();
    protected abstract TelephoneLabel mkTL();
    protected abstract BusinessLabel mkBL();

    public BusinessCard createBusinessCard() {
        BusinessCard card = new BusinessCard();
        card.addAddressLabel(mkAL());
        card.addTelephoneLabel(mkTL());
        card.addBusinessLabel(mkBL());
        return card;
    }
}

// Beispiel 2: Fabrikmethode mit Schnittstelle
interface LabelFactory {
    AddressLabel createAddressLabel();
}

class GermanLabelFactory implements LabelFactory {
    public AddressLabel createAddressLabel() {
        return new GermanAddressLabel();
    }
}

class USLabelFactory implements LabelFactory {
    public AddressLabel createAddressLabel() {
        return new USAddressLabel();
    }
}
```
