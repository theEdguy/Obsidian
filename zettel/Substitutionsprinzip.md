---
id: 198d92e1-3d1b-4972-8f8f-ecc4874342a6
title: "Substitutionsprinzip"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - design_prinzipien
  - polymorphie
  - prinzip
  - lsp
  - draft
source: "software_engineering_kapitel_04"
---

# [[Substitutionsprinzip]]

- **Kernkonzept:** Das [[Substitutionsprinzip]] (auch [[Liskovsches_Substitutionsprinzip|Liskovsches Substitutionsprinzip]], [[LSP]]) ist ein fundamentales [[Prinzip]] der [[Objektorientierung]], das besagt, dass [[Instanz|Instanzen]] einer [[Unterklasse]] überall dort verwendet werden können, wo [[Instanz|Instanzen]] ihrer [[Oberklasse]] erwartet werden, ohne dass sich das [[Verhalten]] des [[Programm|Programms]] unerwartet ändert. Es gewährleistet, dass [[Vererbung|Vererbungshierarchien]] konsistent und typsicher sind und fördert die [[Polymorphie]] sowie [[Erweiterbarkeit]] von [[Software]].
- **Nutzen & Zweck:** Das [[Substitutionsprinzip]] existiert, um die korrekte Verwendung von [[Vererbung]] in der [[Objektorientierung]] sicherzustellen. Es löst das Problem, dass [[Unterklasse|Unterklassen]] die [[Funktionalität]] ihrer [[Oberklasse|Oberklassen]] nicht brechen oder unerwartete [[Seiteneffekt|Seiteneffekte]] verursachen dürfen. Dadurch wird die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Robustheit]] von [[Software]] verbessert, da [[Code]], der mit [[Oberklasse|Oberklassen]] arbeitet, auch mit allen abgeleiteten [[Unterklasse|Klassen]] funktioniert, ohne angepasst werden zu müssen. Es ermöglicht [[Wiederverwendung]] und [[Flexibilität]] im [[Design]], indem es [[Schnittstelle|Schnittstellen]] und [[Invariante|Invarianten]] der [[Oberklasse|Oberklassen]] bewahrt.
- **Abgrenzung & Grenzen:** Das [[Substitutionsprinzip]] sollte nicht genutzt werden, wenn die [[Unterklasse]] die [[Vorbedingung|Vorbedingungen]] der [[Oberklasse]] verschärft, [[Nachbedingung|Nachbedingungen]] abschwächt oder [[Invariante|Invarianten]] verletzt. Es unterscheidet sich von einfacher [[Vererbung]], da es nicht nur die [[Struktur]], sondern auch das [[Verhalten]] der [[Oberklasse]] bewahren muss. Verstöße führen zu unerwartetem [[Verhalten]] oder [[Fehler|Fehlern]] im [[Code]]. Alternativen wie [[Komposition]] oder [[Schnittstelle|Interfaces]] sind vorzuziehen, wenn die [[Vererbung|Vererbungshierarchie]] zu starr oder unnatürlich wirkt, z. B. im [[Quadrat-Rechteck-Problem]], wo eine [[Quadrat]]-Klasse nicht sinnvoll von einer [[Rechteck]]-Klasse erben sollte. Das Prinzip sollte nicht mit semantisch unpassenden [[Ist-eine-Beziehung|„Ist-eine“-Beziehungen]] verwechselt werden, die die [[Kohäsion]] des [[Design|Designs]] beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel 1: Verletzung des Substitutionsprinzips (Quadrat-Rechteck-Problem)
class Rechteck {
    protected int a, b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public void setA(int a) {
        this.a = a;
    }
    
    public void setB(int b) {
        this.b = b;
    }
    
    public int flaeche() {
        return a * b;
    }
}

// Unterklasse verletzt das Prinzip, da sie die Invariante a != b bricht
class Quadrat extends Rechteck {
    public Quadrat(int a) {
        super(a, a);
    }
    
    @Override
    public void setA(int a) {
        this.a = a;
        this.b = a; // Verletzung: b sollte unabhängig bleiben
    }
    
    @Override
    public void setB(int b) {
        this.a = b;
        this.b = b; // Verletzung: a sollte unabhängig bleiben
    }
}

// Beispiel 2: Korrekte Anwendung des Substitutionsprinzips
class Form {
    public int flaeche() {
        return 0;
    }
}

class RechteckKorrekt extends Form {
    protected int a, b;
    
    public RechteckKorrekt(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    @Override
    public int flaeche() {
        return a * b;
    }
}

class QuadratKorrekt extends Form {
    private int seite;
    
    public QuadratKorrekt(int seite) {
        this.seite = seite;
    }
    
    @Override
    public int flaeche() {
        return seite * seite;
    }
}

// Verwendung
Form form1 = new RechteckKorrekt(3, 4); // Erlaubt
Form form2 = new QuadratKorrekt(5);     // Erlaubt, da beide Form erfüllen
```

*Erläuterung:* Im ersten Beispiel verletzt `Quadrat` das [[Substitutionsprinzip]], da es die [[Invariante]] von `Rechteck` (`a` und `b` sind unabhängig) bricht. Im zweiten Beispiel wird das Prinzip durch eine gemeinsame [[Oberklasse]] `Form` eingehalten, die keine [[Invariante|Invarianten]] vorgibt, die von den [[Unterklasse|Unterklassen]] verletzt werden könnten.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Liskovsches_Substitutionsprinzip]]
  - [[Polymorphie]]
