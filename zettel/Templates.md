---
id: 340580e8-4ca2-436b-8e62-823968ec2fc0
title: "Templates"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - paradigma
  - draft
source: "software_engineering_kapitel_03"
---

# [[Templates]]

- **Kernkonzept:** Templates sind ein fundamentaler Mechanismus der Vererbung in der Objektorientierung, der es ermöglicht, neue Objekte basierend auf einer Vorlage (Template) zu erzeugen. Diese Vorlage garantiert, dass die neu erstellten Objekte bestimmte Eigenschaften und Verhaltensweisen der ursprünglichen Klasse übernehmen.
- **Nutzen & Zweck:** Templates lösen das Problem der Wiederverwendung und Standardisierung von Objektstrukturen. Sie ermöglichen die effiziente Erstellung neuer Objekte mit vordefinierten Eigenschaften, ohne diese manuell neu implementieren zu müssen. Dadurch wird Code-Duplikation vermieden, die Wartbarkeit verbessert und die Konsistenz innerhalb eines Systems sichergestellt. Templates sind besonders nützlich, wenn mehrere Objekte ähnliche Grundstrukturen aufweisen, aber spezifische Anpassungen benötigen.
- **Abgrenzung & Grenzen:** Templates sollten nicht genutzt werden, wenn Objekte stark unterschiedliche Strukturen oder Verhaltensweisen aufweisen, die sich nicht sinnvoll aus einer gemeinsamen Vorlage ableiten lassen. Im Vergleich zu Alternativen wie Komposition oder Interfaces bieten Templates weniger Flexibilität, da sie eine starre Vererbungshierarchie voraussetzen. Bei übermäßiger Nutzung können tiefe Vererbungshierarchien entstehen, die schwer zu warten und zu erweitern sind. Zudem sind Templates ungeeignet, wenn dynamische Änderungen zur Laufzeit erforderlich sind, da sie statische Strukturen definieren.
- **Beispiel / Code:** ```java
// Template-Klasse (Vorlage)
class Fahrzeug {
    protected String marke;
    protected int baujahr;
    
    public Fahrzeug(String marke, int baujahr) {
        this.marke = marke;
        this.baujahr = baujahr;
    }
    
    public void anzeigen() {
        System.out.println("Marke: " + marke + ", Baujahr: " + baujahr);
    }
}

// Neue Klasse basierend auf dem Template
class Auto extends Fahrzeug {
    private int anzahlTueren;
    
    public Auto(String marke, int baujahr, int anzahlTueren) {
        super(marke, baujahr);
        this.anzahlTueren = anzahlTueren;
    }
    
    @Override
    public void anzeigen() {
        super.anzeigen();
        System.out.println("Anzahl Türen: " + anzahlTueren);
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        Auto meinAuto = new Auto("VW", 2020, 4);
        meinAuto.anzeigen();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3b
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
