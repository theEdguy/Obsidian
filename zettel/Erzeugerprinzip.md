---
id: 4bb261eb-bf16-4ad2-8cd1-a7c5ef3cdf10
title: "Erzeugerprinzip"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - verantwortung
  - draft
source: "software_engineering_kapitel_13"
---

# [[Erzeugerprinzip]]

- **Kernkonzept:** Das [[Erzeugerprinzip]] ist ein [[Designprinzip]] im [[objektorientiertes_Design|objektorientierten Software-Engineering]], das besagt, dass eine [[Klasse]] für die Erzeugung eines [[Objekt|Objekts]] einer anderen [[Klasse]] verantwortlich sein sollte, wenn sie diese enthält, eng mit ihr zusammenarbeitet oder alle notwendigen [[Information|Informationen]] für deren Initialisierung besitzt.
- **Nutzen & Zweck:** Das [[Erzeugerprinzip]] existiert, um die [[Verantwortlichkeit|Verantwortlichkeiten]] bei der [[Objekterzeugung]] klar zu verteilen und die [[Kopplung]] zwischen [[Klasse|Klassen]] zu minimieren. Es löst das Problem, dass [[Objekterzeugung|Objekterzeugungen]] oft willkürlich oder an ungeeigneten Stellen im [[Code]] erfolgen, was zu schwer wartbaren und unübersichtlichen [[System|Systemen]] führt. Durch die Anwendung des Prinzips wird sichergestellt, dass die Erzeugung von [[Objekt|Objekten]] dort stattfindet, wo das notwendige Wissen und die [[Daten]] dafür vorhanden sind. Dies erhöht die [[Kohäsion]] und verbessert die [[Wartbarkeit]], da die [[Logik]] der Erzeugung nahe an den [[Daten]] liegt, die für die Initialisierung benötigt werden.
- **Abgrenzung & Grenzen:** Das [[Erzeugerprinzip]] sollte nicht angewendet werden, wenn die Erzeugung eines [[Objekt|Objekts]] komplexe [[Abhängigkeit|Abhängigkeiten]] oder externe [[Ressource|Ressourcen]] erfordert, die nicht in der erzeugenden [[Klasse]] vorhanden sind. In solchen Fällen können Alternativen wie [[Factory_Method_(Entwurfsmuster)|Fabriken]], [[Builder_Pattern|Builder]] oder [[Dependency_Injection]] sinnvoller sein. Zudem unterscheidet es sich vom [[Information_Expert_Principle|Experten-Prinzip]], das sich auf die Zuweisung von [[Verantwortlichkeit|Verantwortlichkeiten]] für die Durchführung von Aufgaben konzentriert, während das [[Erzeugerprinzip]] speziell die [[Objekterzeugung]] adressiert. Es ist auch nicht geeignet, wenn die Erzeugung logisch in eine zentrale [[Instanz]] (z. B. eine [[Factory_Method_(Entwurfsmuster)|Factory-Klasse]]) ausgelagert werden soll, um die [[Flexibilität]] zu erhöhen oder die [[Lose_Kopplung|lose Kopplung]] zu fördern.
- **Beispiel / Code:** ```java
// Beispiel 1: Erzeugung durch eine Klasse, die die notwendigen Informationen besitzt
class Order {
    private List<Item> items;

    public Item createItem(String name, double price) {
        // Order kennt die Struktur der Items und kann sie erzeugen
        Item item = new Item(name, price);
        items.add(item);
        return item;
    }
}

// Beispiel 2: Erzeugung einer Bestellposition durch die Bestellung
public class Bestellung {
    private List<Bestellposition> positionen;
    
    public Bestellposition neuePositionErstellen(Produkt produkt, int menge) {
        Bestellposition position = new Bestellposition(produkt, menge);
        positionen.add(position);
        return position;
    }
}

public class Bestellposition {
    private Produkt produkt;
    private int menge;
    
    public Bestellposition(Produkt produkt, int menge) {
        this.produkt = produkt;
        this.menge = menge;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a2
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
