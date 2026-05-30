---
id: 6ae23378-af5a-4ca0-8aae-d5208b5a7ebc
title: "Erzeugerprinzip"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Erzeugerprinzip]]

- **Kernkonzept:** Das [[Erzeugerprinzip]] ist ein [[Designprinzip]], das besagt, dass eine [[Klasse]] für die Erzeugung einer anderen [[Klasse]] verantwortlich sein sollte, wenn sie diese enthält oder alle notwendigen [[Information|Informationen]] für deren Initialisierung besitzt.
- **Nutzen & Zweck:** Es fördert die [[Kohäsion]] und [[Wartbarkeit]], indem die Erzeugung von [[Objekt|Objekten]] dort erfolgt, wo das notwendige Wissen vorhanden ist.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die Erzeugung [[Komplexität]] in eine [[Klasse]] verlagert, die bereits viele [[Verantwortlichkeit|Verantwortlichkeiten]] hat. Unterscheidet sich von [[Factory_Method_(Entwurfsmuster)|Factory-Methoden]], die die Erzeugung abstrahieren.
- **Beispiel / Code:** ```java
class Order {
    private List<Item> items;

    public Item createItem(String name, double price) {
        // Order kennt die Struktur der Items und kann sie erzeugen
        Item item = new Item(name, price);
        items.add(item);
        return item;
    }
}
```
