---
id: 0307f7de-a305-4323-be83-b08ab4d562d2
title: "Komposition_über_Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - design_prinzipien
  - objektorientierung
  - entwurfsmuster
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Komposition_über_Vererbung]]

- **Kernkonzept:** Ein [[Designprinzip]], das besagt, dass [[Komposition]] (Zusammenfügen von [[Objekt|Objekten]]) der [[Vererbung_(OOP)|Vererbung]] vorzuziehen ist, um [[Flexibilität]] und [[Wiederverwendung]] zu erhöhen.
- **Nutzen & Zweck:** Vermeidet die [[Starke_Kopplung|starke Kopplung]] und [[Rigidität]] von [[Vererbung_(OOP)|Vererbungshierarchien]]. Ermöglicht dynamische Änderungen zur [[Laufzeit]] und fördert [[Lose_Kopplung|lose Kopplung]] sowie [[Kohäsion]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn eine echte [[Ist-eine-Beziehung]] vorliegt (z. B. „Ein [[Spieler]] ist ein [[Mitglied]]“). Kann zu mehr [[Boilerplate-Code]] führen, wenn viele [[Delegation|Delegationen]] nötig sind.
- **Beispiel / Code:** ```java
// Komposition statt Vererbung
class Rechteck {
    private int a, b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public int flaeche() {
        return a * b;
    }
}

class Quadrat {
    private Rechteck rechteck;
    
    public Quadrat(int a) {
        this.rechteck = new Rechteck(a, a);
    }
    
    public int flaeche() {
        return rechteck.flaeche();
    }
}
```
