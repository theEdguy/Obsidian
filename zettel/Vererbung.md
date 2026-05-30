---
id: 40a132ab-5139-428d-ac5b-dfbfd03aa5ca
title: "Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - oop
  - vererbung
  - draft
source: "SWE Slides (Folien 1-15)"
---

# [[Vererbung]]

- **Kernkonzept:** Ein [[Mechanismus]] der [[Objektorientierung]], bei dem eine [[Klasse]] die [[Eigenschaft|Eigenschaften]] und [[Methode|Methoden]] einer anderen [[Klasse]] erbt, um [[Wiederverwendbarkeit]] und [[Hierarchie]] zu ermöglichen.
- **Nutzen & Zweck:** Reduziert [[Redundanz]] im [[Code]] und ermöglicht die [[Spezialisierung]] von [[Klasse|Klassen]] durch Erweiterung oder Überschreibung von [[Verhalten]].
- **Abgrenzung & Grenzen:** Kann zu [[Starke_Kopplung|starker Kopplung]] und [[Fragile_Base_Class_Problem|fragilen Basisklassen]] führen. Oft durch [[Komposition]] oder [[Interface|Interfaces]] ersetzbar, um [[Flexibilität]] zu erhöhen.
- **Beispiel / Code:** ```java
// Beispiel für [[Vererbung]]
class Fahrzeug {
    void fahren() {
        System.out.println("Fahrzeug fährt");
    }
}

class Auto extends Fahrzeug {
    @Override
    void fahren() {
        System.out.println("Auto fährt mit 4 Rädern");
    }
}
```
