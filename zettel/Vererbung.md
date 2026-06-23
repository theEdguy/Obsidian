---
id: cf6cd643-daa3-4ddd-b300-45245458d4fb
title: "Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - objektorientierung
  - paradigma
  - uml
  - klassendiagramm
  - beziehung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Vererbung]]

- **Kernkonzept:** Ein zentraler [[Mechanismus]] der [[Objektorientierung]], bei dem eine [[Klasse|Unterklasse]] die [[Eigenschaft|Eigenschaften]] und [[Methode|Methoden]] einer [[Klasse|Oberklasse]] erbt, um [[Wiederverwendbarkeit]] und hierarchische [[Struktur|Strukturen]] („ist-ein“-Beziehungen) im [[Klassendiagramm]] zu modellieren. Durch [[Vererbung]] können [[Unterklasse|Unterklassen]] die Funktionalität der Oberklasse erweitern, überschreiben oder anpassen, wobei das [[Liskovsches_Substitutionsprinzip]] sicherstellt, dass [[Instanz|Instanzen]] der [[Unterklasse|Unterklassen]] auch als [[Instanz|Instanzen]] der Oberklasse behandelt werden können.
- **Nutzen & Zweck:** [[Vererbung]] reduziert [[Redundanz]] im [[Code]] und fördert die [[Modularität]] sowie [[Wartbarkeit]] von Software, indem gemeinsame [[Eigenschaft|Eigenschaften]] und [[Methode|Methoden]] in einer Oberklasse zentralisiert werden. Änderungen in der Oberklasse wirken sich automatisch auf alle [[Unterklasse|Unterklassen]] aus, was die [[Erweiterbarkeit]] des Systems vereinfacht. Zudem ermöglicht sie die Umsetzung von [[Polymorphie]], wodurch [[Objekt|Objekte]] unterschiedlicher [[Klasse|Klassen]] über eine gemeinsame [[Schnittstelle]] einheitlich behandelt werden können. Dies unterstützt die [[Abstraktion]] und [[Kapselung]] im [[Softwareentwurf]] und begünstigt flexible, erweiterbare [[Architektur|Architekturen]]. Durch das [[Liskovsches_Substitutionsprinzip]] wird sichergestellt, dass [[Unterklasse|Unterklassen]] ohne Verletzung der Semantik anstelle der Oberklasse verwendet werden können, was die [[Wiederverwendbarkeit]] und [[Konsistenz]] des Systems erhöht. [[Vererbung]] löst das Problem der [[Redundanz]] und verbessert die Strukturierung von [[Software-System|Software-Systemen]], indem sie hierarchische [[Beziehung|Beziehungen]] im [[Klassendiagramm]] abbildet.
- **Abgrenzung & Grenzen:** [[Vererbung]] sollte nur eingesetzt werden, wenn eine echte „ist-ein“-Beziehung zwischen den [[Klasse|Klassen]] besteht, da sonst unklare [[Hierarchie|Hierarchien]], [[Starke_Kopplung|starke Kopplung]] und das [[Fragile_Base_Class_Problem]] entstehen. Tiefe [[Vererbungshierarchie|Vererbungshierarchien]] können die [[Wartbarkeit]] und [[Testbarkeit]] beeinträchtigen, da Änderungen in der Oberklasse unerwartete Auswirkungen auf [[Unterklasse|Unterklassen]] haben. Alternativen wie [[Komposition]] („hat-ein“-Beziehung), [[Aggregation]] oder [[Interface|Interfaces]] sind oft vorzuziehen, insbesondere wenn [[Objekt|Objekte]] dynamisch ausgetauscht oder kombiniert werden müssen. Bei Mehrfachvererbung (nicht in allen [[Programmiersprache|Programmiersprachen]] unterstützt) können Konflikte durch überlappende [[Eigenschaft|Eigenschaften]] oder [[Methode|Methoden]] entstehen. Zudem ist [[Vererbung]] statisch und kann zur Laufzeit nicht geändert werden, was die [[Flexibilität]] einschränkt. Übermäßige [[Vererbung]] kann die [[Kohäsion]] verringern, wenn [[Klasse|Klassen]] Funktionalitäten erben, die nicht zu ihrem eigentlichen Zweck passen. Besonders problematisch ist die Verletzung des [[Liskovsches_Substitutionsprinzip|Substitutionsprinzips]], wie im Beispiel eines [[Quadrat|Quadrats]], das von einem [[Rechteck]] erbt, aber dessen Semantik (z. B. unabhängige Seitenlängen) nicht erfüllt. [[Vererbung]] sollte nicht genutzt werden, wenn keine echte hierarchische Beziehung vorliegt, da dies zu unnötiger [[Komplexität]] führt.
- **Beispiel / Code:** ```java
// Beispiel 1: Grundlegende Vererbung mit Überschreibung und Substitutionsprinzip
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

// Beispiel 2: Vererbung mit Konstruktoraufruf und Erweiterung
class Mitglied {
    private String name;
    private String adresse;
    
    public Mitglied(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
    }
    
    public void vorstellen() {
        System.out.println("Hallo, ich bin " + name);
    }
}

class PremiumMitglied extends Mitglied {
    private int bonusPunkte;
    
    public PremiumMitglied(String name, String adresse, int bonusPunkte) {
        super(name, adresse); // Aufruf des Konstruktors der Oberklasse
        this.bonusPunkte = bonusPunkte;
    }
    
    public void bonusAnzeigen() {
        System.out.println("Bonus: " + bonusPunkte);
    }
}

// Beispiel 3: Vererbung mit Semantik-Problem (Verletzung des Liskovschen Substitutionsprinzips)
class Rechteck {
    protected int a;
    protected int b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
    
    public int flaeche() {
        return a * b;
    }
}

class Quadrat extends Rechteck {
    public Quadrat(int seitenlaenge) {
        super(seitenlaenge, seitenlaenge); // Aufruf des Oberklassen-Konstruktors
    }
    
    @Override
    public void stretch(int i, int j) {
        // Überschreiben der Methode, um die Quadrat-Eigenschaft (a = b) zu erhalten
        this.a += i;
        this.b = this.a; // Sicherstellen, dass a = b bleibt (Verletzung der Rechteck-Semantik)
    }
}

// Beispiel 4: Vererbung im Klassendiagramm (Fahrzeug-Hierarchie)
class Fahrzeug {
    protected String hersteller;
    
    public Fahrzeug(String hersteller) {
        this.hersteller = hersteller;
    }
    
    public void starten() {
        System.out.println("Fahrzeug wird gestartet.");
    }
}

class Auto extends Fahrzeug {
    private int anzahlTueren;
    
    public Auto(String hersteller, int anzahlTueren) {
        super(hersteller);
        this.anzahlTueren = anzahlTueren;
    }
    
    @Override
    public void starten() {
        System.out.println("Auto von " + hersteller + " wird gestartet.");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a4
- **Vorgänger / Parent:** [[Klassendiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Klassendiagramm]]
  - [[Objektorientierte_Programmierung]]
