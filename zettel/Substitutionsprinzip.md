---
id: f6304d27-4fa0-45af-8758-e0d0f965563f
title: "Substitutionsprinzip"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - design_prinzipien
  - polymorphie
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Substitutionsprinzip]]

- **Kernkonzept:** Ein [[Prinzip]] der [[Objektorientierung]], das besagt, dass [[Instanz|Instanzen]] einer [[Unterklasse]] überall dort verwendet werden können, wo [[Instanz|Instanzen]] ihrer [[Oberklasse]] erwartet werden, ohne dass das Programm fehlerhaft wird.
- **Nutzen & Zweck:** Ermöglicht [[Polymorphie]] und [[Erweiterbarkeit]] von [[Software]], indem es sicherstellt, dass [[Unterklasse|Unterklassen]] die [[Schnittstelle]] und das [[Verhalten]] ihrer [[Oberklasse]] einhalten. Fördert die [[Wiederverwendung]] und [[Flexibilität]] im [[Design]].
- **Abgrenzung & Grenzen:** Verstöße gegen das [[Prinzip]] führen zu unerwartetem [[Verhalten]] oder [[Fehler|Fehlern]] im [[Code]]. Nicht anwendbar, wenn die [[Unterklasse]] die [[Schnittstelle]] oder [[Invariante|Invarianten]] der [[Oberklasse]] verletzt. Sollte nicht mit [[Ist-eine-Beziehung|„Ist-eine“-Beziehungen]] verwechselt werden, die semantisch nicht passen (z. B. [[Quadrat]] und [[Rechteck]]).
- **Beispiel / Code:** ```java
// Oberklasse
class Rechteck {
    protected int a, b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public int flaeche() {
        return a * b;
    }
}

// Unterklasse (verletzt das Substitutionsprinzip)
class Quadrat extends Rechteck {
    public Quadrat(int a) {
        super(a, a);
    }
    
    @Override
    public void setA(int a) {
        this.a = a;
        this.b = a; // Verletzung: b sollte unabhängig bleiben
    }
}
```

*Problem:* `Quadrat` kann nicht als `Rechteck` substituiert werden, ohne die [[Invariante]] `a != b` zu brechen.
