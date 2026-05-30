---
id: 16a2b973-3b03-49c0-a99e-7a1c4f3f6921
title: "Kohäsion"
date: 2026-05-30
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - design_principle
  - oop
  - draft
source: "SWE Slides (Folien 331-345)"
---

# [[Kohäsion]]

- **Kernkonzept:** [[Kohäsion]] ist ein [[Designprinzip]], das beschreibt, wie stark die [[Funktionalität|Funktionalitäten]] und [[Verantwortung|Verantwortungen]] einer [[Klasse]] oder eines [[Modul|Moduls]] miteinander in Beziehung stehen und ein gemeinsames, klar definiertes [[Ziel]] verfolgen. Hohe [[Kohäsion]] bedeutet, dass eine [[Klasse]] oder ein [[Modul]] eine fokussierte [[Aufgabe]] erfüllt und ihre [[Element|Elemente]] eng zusammenarbeiten, um diese zu erreichen.
- **Nutzen & Zweck:** [[Kohäsion]] löst das [[Problem]] der [[Unübersichtlichkeit]] und [[Schwerwartbarkeit]] von [[Code]], indem sie sicherstellt, dass [[Klasse|Klassen]] und [[Modul|Module]] eine einzige, klar abgegrenzte [[Verantwortung]] übernehmen. Dadurch wird die [[Lesbarkeit]], [[Wiederverwendbarkeit]], [[Testbarkeit]] und [[Modularität]] des [[Systems]] verbessert. Hohe [[Kohäsion]] erleichtert zudem das [[Refactoring]] und die [[Fehlerbehebung]], da [[Änderung|Änderungen]] lokal begrenzt bleiben und weniger [[Abhängigkeit|Abhängigkeiten]] zu anderen [[Teil|Teilen]] des [[Systems]] bestehen.
- **Abgrenzung & Grenzen:** Hohe [[Kohäsion]] ist nicht immer einfach umzusetzen, insbesondere wenn [[Anforderung|Anforderungen]] komplex, widersprüchlich oder unklar sind. Ein übermäßiger Fokus auf [[Kohäsion]] kann zu einer Zersplitterung des [[Codes]] in viele kleine [[Klasse|Klassen]] oder [[Modul|Module]] führen, was die [[Komplexität]] des [[Systems]] erhöhen und die [[Navigierbarkeit]] erschweren kann. Zudem darf [[Kohäsion]] nicht mit [[Lose_Kopplung]] verwechselt werden: Während [[Kohäsion]] die innere Stärke einer [[Klasse]] oder eines [[Modul|Moduls]] beschreibt, bezieht sich [[Lose_Kopplung]] auf die Minimierung der [[Abhängigkeit|Abhängigkeiten]] zwischen ihnen. Ein Verstoß gegen das [[Single_Responsibility_Principle]] führt oft zu [[Geringe_Kohäsion|geringer Kohäsion]], da eine [[Klasse]] zu viele [[Verantwortlichkeit|Verantwortlichkeiten]] übernimmt.
- **Beispiel / Code:** ```java
// Beispiel für hohe Kohäsion: Jede Klasse hat eine klare, fokussierte Verantwortung
class Order {
    private List<Item> items;

    public double calculateTotal() {
        return items.stream().mapToDouble(Item::getPrice).sum();
    }

    public void addItem(Item item) {
        items.add(item);
    }
}

// Weitere Beispiele für hohe Kohäsion durch klare Aufgabentrennung
public class AddressLabel {
    private String address;

    public String format() {
        return "Address: " + address;
    }
}

public class TelephoneLabel {
    private String phoneNumber;

    public String format() {
        return "Phone: " + phoneNumber;
    }
}
```
