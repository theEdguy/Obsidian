---
id: 52eb4baf-6e2d-4084-b88a-25432449a5df
title: "Adapter_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - strukturmuster
  - design_pattern
  - architektur
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Adapter_Pattern]]

- **Kernkonzept:** Das [[Adapter_Pattern]] ist ein [[Strukturmuster|Strukturmuster]], das eine [[Schnittstelle]] in eine andere [[Schnittstelle|Schnittstelle]] umwandelt, um inkompatible [[Klasse|Klassen]] zusammenarbeiten zu lassen. Es führt eine vermittelnde [[Klasse]] (den Adapter) ein, die die [[Schnittstelle]] des [[Client|Clients]] an die der vorhandenen [[Klasse]] anpasst.
- **Nutzen & Zweck:** Das [[Adapter_Pattern]] ermöglicht die [[Integration]] von [[Komponente|Komponenten]] mit inkompatiblen [[Schnittstelle|Schnittstellen]], ohne deren [[Code]] zu ändern. Es löst das Problem der Wiederverwendung bestehender [[Klasse|Klassen]] oder [[Bibliothek|Bibliotheken]], deren [[Schnittstelle|Schnittstellen]] nicht zur gewünschten [[Schnittstelle]] passen, und vermeidet so Änderungen am bestehenden [[Code]] oder die Neuentwicklung von [[Funktionalität]]. Dadurch fördert es [[Wiederverwendbarkeit]] und [[Flexibilität]] im [[Softwaredesign]].
- **Abgrenzung & Grenzen:** Das [[Adapter_Pattern]] kann zu [[Überkomplexität]] führen, wenn zu viele [[Adapter]] benötigt werden. Es ist nicht geeignet, wenn die [[Schnittstelle|Schnittstellen]] bereits kompatibel sind oder wenn die Anpassung zu komplex wird. Zudem ist es ungeeignet für [[Performance]]-kritische Szenarien oder wenn die [[Schnittstelle|Schnittstellen]] grundlegend inkompatibel sind. Es unterscheidet sich vom [[Bridge_Pattern]], da es bestehende [[Schnittstelle|Schnittstellen]] anpasst, statt eine stabile [[Abstraktion]] für variable [[Implementierung|Implementierungen]] zu schaffen.
- **Beispiel / Code:** ```java
// Beispiel für das [[Adapter_Pattern]] (Objekt-Adapter)

// Ziel-Schnittstelle, die der Client erwartet
interface Target {
    void targetOp();
}

// Bestehende Klasse mit inkompatibler Schnittstelle
class Adaptee {
    void existingOp() {
        System.out.println("Logik der bestehenden Methode");
    }
}

// Adapter, der die Ziel-Schnittstelle implementiert und die bestehende Klasse einbindet
class Adapter implements Target {
    private Adaptee adaptee;
    
    Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    
    @Override
    public void targetOp() {
        adaptee.existingOp();
    }
}

// Beispiel für Klassen-Adapter (Java unterstützt keine Mehrfachvererbung, daher seltener genutzt)
interface ModerneSchnittstelle {
    void neueMethode();
}

class AlteKlasse {
    void alteMethode() {
        System.out.println("Alte Methode");
    }
}

class AdapterKlassenVariante extends AlteKlasse implements ModerneSchnittstelle {
    @Override
    public void neueMethode() {
        alteMethode();
    }
}
```
