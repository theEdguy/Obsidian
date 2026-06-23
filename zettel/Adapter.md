---
id: 5aeec504-187e-4366-befd-f789bc0c3a13
title: "Adapter"
date: 2026-06-24
tags:
  - software_engineering
  - adapter
  - design_pattern
  - strukturmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[Adapter]]

- **Kernkonzept:** Der [[Adapter]] ist ein [[strukturelles_Entwurfsmuster|strukturelles Entwurfsmuster]], das die [[Schnittstelle]] einer [[Klasse]] in eine andere, vom [[Client]] erwartete [[Schnittstelle]] umwandelt. Es ermöglicht die Zusammenarbeit von [[Klassen]], die aufgrund inkompatibler [[Schnittstellen]] nicht direkt interagieren könnten, ohne deren [[Quellcode]] zu modifizieren.
- **Nutzen & Zweck:** Der [[Adapter]] existiert, um [[Inkompatibilität|Inkompatibilitäten]] zwischen bestehenden [[Systemen]], [[Bibliotheken]] oder [[Komponenten]] zu überbrücken, ohne deren [[Quellcode]] ändern zu müssen. Er löst das konkrete Problem, dass vorhandene [[Implementierungen]] nicht nahtlos integriert werden können, weil ihre [[Schnittstellen]] nicht zur benötigten [[Schnittstelle]] passen. Dadurch fördert er die [[Wiederverwendbarkeit]] von [[Code]] und reduziert [[Abhängigkeiten]], indem er eine vermittelnde [[Schicht]] einführt, die die [[Kommunikation]] zwischen inkompatiblen [[Komponenten]] ermöglicht. Der [[Adapter]] reduziert zudem den Aufwand für [[Anpassungen]] und unterstützt die [[Modularität]] von [[Software]]-Systemen.
- **Abgrenzung & Grenzen:** Der [[Adapter]] sollte nicht genutzt werden, wenn die [[Schnittstellen]] der zu verbindenden [[Klassen]] bereits kompatibel sind oder wenn eine einfache [[Anpassung]] des [[Quellcodes]] der bestehenden [[Klasse]] möglich und sinnvoller ist. Im Vergleich zu anderen [[Entwurfsmuster|Mustern]] wie dem [[Fassade|Fassade-Muster]], das eine vereinfachte [[Schnittstelle]] zu einem komplexen [[Subsystem]] bietet, konzentriert sich der [[Adapter]] auf die [[Anpassung]] einer einzelnen [[Klasse]] oder [[Komponente]]. Zudem unterscheidet er sich von der [[Brücke|Brücke-Pattern]], die von vornherein eine [[Abstraktion]] von ihrer [[Implementierung]] entkoppelt, um unabhängige [[Variationen]] zu ermöglichen. Der [[Adapter]] ist weniger geeignet, wenn die anzupassende [[Klasse]] häufigen [[Änderungen]] unterliegt, da dies zu hohem [[Wartungsaufwand]] führen kann. Bei kritischen [[Performance|Performance-Anforderungen]] sollte der zusätzliche [[Overhead]] der [[Abstraktionsebene]] berücksichtigt werden, da dieser die [[Effizienz]] beeinträchtigen kann.
- **Beispiel / Code:** ```java
// Ziel-Schnittstelle, die der Client erwartet
interface ZielSchnittstelle {
    void erwarteteMethode();
}

// Bestehende Klasse mit inkompatibler Schnittstelle
class Adaptee {
    void spezifischeMethode() {
        System.out.println("Spezifische Methode des Adaptee aufgerufen");
    }
}

// Adapter-Klasse, die die Schnittstelle anpasst (Objekt-Adapter)
class Adapter implements ZielSchnittstelle {
    private Adaptee adaptee;

    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }

    @Override
    public void erwarteteMethode() {
        adaptee.spezifischeMethode();
    }
}

// Alternative Implementierung: Klassen-Adapter (nur in Sprachen mit Mehrfachvererbung möglich)
// class Adapter extends Adaptee implements ZielSchnittstelle {
//     @Override
//     public void erwarteteMethode() {
//         spezifischeMethode();
//     }
// }

// Client-Code
public class Client {
    public static void main(String[] args) {
        Adaptee adaptee = new Adaptee();
        ZielSchnittstelle adapter = new Adapter(adaptee);
        adapter.erwarteteMethode(); // Ruft die spezifische Methode des Adaptee auf
    }
}
```

**Hinweis:** Der gezeigte [[Adapter]] ist ein *Objekt-Adapter*, der [[Komposition]] nutzt. In Sprachen mit [[Mehrfachvererbung]] (z. B. C++) kann auch ein *Klassen-Adapter* verwendet werden, der [[Vererbung]] einsetzt (im Code als Kommentar angedeutet). Beide Varianten erfüllen denselben Zweck, unterscheiden sich jedoch in ihrer [[Implementierung]] und [[Flexibilität]].
