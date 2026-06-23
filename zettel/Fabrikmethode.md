---
id: ab5612d3-a278-49dc-9451-672e9b248ac4
title: "Fabrikmethode"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - software_architecture
  - oop
  - erzeugungsmuster
  - erzeugung
  - fabrik
  - draft
source: "software_engineering_kapitel_14"
---

# [[Fabrikmethode]]

- **Kernkonzept:** Die [[Fabrikmethode]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]] in der [[objektorientierten_Programmierung|objektorientierten Programmierung]], das eine [[Schnittstelle]] zur [[Erstellung]] von [[Objekt|Objekten]] definiert, aber die konkrete [[Klasse]] der zu erzeugenden [[Objekt|Objekte]] an [[Unterklasse|Unterklassen]] delegiert. Sie ermöglicht die [[Entkopplung]] von [[Client-Code]] und konkreten [[Klasse|Klassen]], indem die [[Erstellung]] in [[Unterklasse|Unterklassen]] verlagert wird und fördert so [[Lose_Kopplung|lose Kopplung]] sowie [[Erweiterbarkeit]].
- **Nutzen & Zweck:** Die [[Fabrikmethode]] löst das [[Problem]], dass eine [[Klasse]] die konkreten [[Klasse|Klassen]] der [[Objekt|Objekte]], die sie erzeugen muss, nicht im Voraus kennen kann. Sie delegiert die Verantwortung für die [[Objekterzeugung]] an [[Unterklasse|Unterklassen]], was die [[Flexibilität]] und [[Erweiterbarkeit]] des [[Code]]s erhöht. Dadurch wird die [[Kopplung]] zwischen [[Klasse|Klassen]] reduziert, und es wird einfacher, neue [[Produkt|Produkte]] oder [[Produkt|Produkttypen]] hinzuzufügen, ohne bestehenden [[Code]] zu ändern. Dies fördert die [[Wiederverwendbarkeit]] und unterstützt [[Designprinzipien]] wie das [[Open-Closed_Principle|Open-Closed-Prinzip]], da [[Erweiterungen]] ohne Modifikation des bestehenden [[Code]]s möglich sind. Besonders nützlich ist die [[Fabrikmethode]], wenn die genaue [[Klasse]] der zu erzeugenden [[Objekt|Objekte]] erst zur [[Laufzeit]] bestimmt werden kann oder wenn [[Variabilität]] in der [[Erstellung]] benötigt wird.
- **Abgrenzung & Grenzen:** Die [[Fabrikmethode]] ist nicht geeignet, wenn die [[Objekterzeugung]] trivial ist oder keine [[Variabilität]] benötigt wird, da sie zusätzlichen [[Overhead]] durch die Definition von [[Unterklasse|Unterklassen]] und [[Schnittstelle|Schnittstellen]] mit sich bringt. Im Vergleich zur [[Abstrakte_Fabrik_(Abstract_Factory)|abstrakten Fabrik]] unterstützt sie nur die [[Erstellung]] eines einzelnen [[Produkt|Produkts]], nicht einer ganzen [[Produktfamilie]]. Sie ist daher weniger komplex, aber auch weniger mächtig, wenn mehrere zusammenhängende [[Objekt|Objekte]] aufeinander abgestimmt erzeugt werden müssen. Im Gegensatz zur [[Template_Methode]] liegt der Fokus hier auf der [[Erstellung]] von [[Objekt|Objekten]] und nicht auf der Definition eines [[Algorithmus|Algorithmusgerüsts]]. Zudem sollte die [[Fabrikmethode]] nicht verwendet werden, wenn keine [[Erweiterbarkeit]] oder [[Flexibilität]] in der [[Objekterzeugung]] erforderlich ist, da sie sonst unnötige [[Komplexität]] einführt.
- **Beispiel / Code:** ```java
// Beispiel 1: Grundlegende Fabrikmethode mit mehreren Label-Typen
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

// Beispiel 2: Fabrikmethode mit Schnittstelle für verschiedene Adressformate
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

// Beispiel 3: Vereinfachte Fabrikmethode für ein einzelnes Produkt
abstract class AddressBook {
    protected abstract AddressLabel mkAL();

    public BusinessCard createBusinessCard() {
        BusinessCard card = new BusinessCard();
        AddressLabel al = mkAL();
        card.addAddressLabel(al);
        return card;
    }
}

class FrenchAddressBook extends AddressBook {
    protected AddressLabel mkAL() {
        return new FrenchAL();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a
- **Vorgänger / Parent:** [[Erzeugungsmuster]]
- **Folgezettel / Unterzettel:**
  - [[Zweck_der_Fabrikmethode]]
  - [[Anwendbarkeit_der_Fabrikmethode]]
  - [[Konsequenzen_der_Fabrikmethode]]
  - [[Beispiel_Adressbuch]]
- **Querverweise:**
  - [[Abstrakte_Fabrik]]
  - [[Erzeugungsprozess]]
