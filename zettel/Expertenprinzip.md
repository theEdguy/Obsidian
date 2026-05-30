---
id: 0e71755f-ebba-4f15-ab10-ef6469e03812
title: "Expertenprinzip"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Expertenprinzip]]

- **Kernkonzept:** Das [[Expertenprinzip]] ist ein [[Designprinzip]], das besagt, dass eine [[Verantwortlichkeit]] der [[Klasse]] zugewiesen werden sollte, die über die meisten [[Information|Informationen]] zur Erfüllung dieser [[Verantwortlichkeit]] verfügt.
- **Nutzen & Zweck:** Es fördert die [[Kohäsion]] und [[Wartbarkeit]] von [[Klasse|Klassen]], indem [[Verantwortlichkeit|Verantwortlichkeiten]] dort angesiedelt werden, wo das notwendige Wissen vorhanden ist.
- **Abgrenzung & Grenzen:** Nicht anwendbar, wenn die [[Klasse]] mit der meisten [[Information]] bereits zu viele [[Verantwortlichkeit|Verantwortlichkeiten]] hat (Verstoß gegen [[Single_Responsibility_Principle]]).
- **Beispiel / Code:** ```java
class Order {
    private List<Item> items;

    public double calculateTotal() {
        // Order kennt die Items und kann den Gesamtpreis berechnen
        return items.stream().mapToDouble(Item::getPrice).sum();
    }
}
```
