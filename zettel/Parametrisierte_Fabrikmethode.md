---
id: 5d952331-a2aa-4b82-a6bf-94126833122a
title: "Parametrisierte_Fabrikmethode"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - software_architecture
  - oop
  - draft
source: "SWE Slides (Folien 331-345)"
---

# [[Parametrisierte_Fabrikmethode]]

- **Kernkonzept:** Eine [[Parametrisierte_Fabrikmethode|parametrisierte Fabrikmethode]] ist eine [[Fabrikmethode]], die durch [[Parameter]] gesteuert wird, um unterschiedliche [[Objekt|Objekte]] zu erzeugen.
- **Nutzen & Zweck:** Sie löst das [[Problem]] der [[Erweiterbarkeit]] bei der [[Objekterzeugung]], indem sie die [[Erstellung]] verschiedener [[Objekt|Objekte]] über [[Parameter]] ermöglicht, ohne den [[Client-Code]] zu ändern. Dadurch wird die [[Flexibilität]] erhöht und [[Boilerplate-Code]] reduziert.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Objekterzeugung]] trivial ist oder keine [[Variabilität]] benötigt wird. Im Vergleich zu nicht-parametrisierten [[Fabrikmethode|Fabrikmethoden]] erhöht sie die [[Komplexität]] und kann zu [[Fehleranfälligkeit]] durch ungültige [[Parameter]] führen.
- **Beispiel / Code:** ```java
class AddressBook {
    protected AddressLabel mkAL(String type) {
        if (type.equals("french")) return new FrenchAL();
        if (type.equals("german")) return new GermanAL();
        return new AddressLabel();
    }
}
```
