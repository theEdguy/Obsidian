---
id: 26e19520-3cef-45a7-b4b4-1676128a1664
title: "Objekt-Adapter"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - adapter_variante
  - draft
source: "software_engineering_kapitel_15"
---

# [[Objekt-Adapter]]

- **Kernkonzept:** Der Objekt-Adapter ist ein strukturelles Entwurfsmuster, das eine bestehende Klasse (Adaptee) mit einer inkompatiblen Schnittstelle durch eine zusätzliche Indirektionsschicht (Adapter) an eine gewünschte Zielschnittstelle anpasst, ohne die ursprüngliche Klasse zu verändern. Dabei hält der Adapter eine Referenz auf das Adaptee-Objekt und leitet Anfragen an dieses weiter.
- **Nutzen & Zweck:** Das Muster existiert, um Inkompatibilitäten zwischen bestehenden Klassen und benötigten Schnittstellen zu überwinden, ohne die ursprünglichen Klassen modifizieren zu müssen. Es ermöglicht die Wiederverwendung von Klassen mit unbekannten oder unpassenden Schnittstellen und fördert die Zusammenarbeit zwischen unabhängig entwickelten Komponenten. Besonders nützlich ist es, wenn Bibliotheken oder Frameworks genutzt werden sollen, deren Schnittstellen nicht direkt zur eigenen Codebasis passen.
- **Abgrenzung & Grenzen:** Der Objekt-Adapter sollte nicht genutzt werden, wenn die anzupassende Klasse bereits die gewünschte Schnittstelle implementiert oder wenn die Anpassung nur temporär benötigt wird. Im Vergleich zum Klassen-Adapter (der Mehrfachvererbung erfordert) ist der Objekt-Adapter flexibler, da er auch mit Unterklassen des Adaptees zusammenarbeitet, erfordert jedoch etwas mehr Aufwand bei der Implementierung. Bei einfachen Schnittstellenanpassungen kann ein direkter Wrapper oder eine einfache Delegation ausreichen. Zudem ist das Muster ungeeignet, wenn die anzupassende Klasse häufig geändert wird, da dies zu Anpassungen im Adapter führen kann.
- **Beispiel / Code:** ```java
// Zielschnittstelle
interface ZielSchnittstelle {
    void operation();
}

// Bestehende Klasse mit inkompatibler Schnittstelle
class Adaptee {
    void spezifischeOperation() {
        System.out.println("Spezifische Operation des Adaptee");
    }
}

// Objekt-Adapter
class Adapter implements ZielSchnittstelle {
    private Adaptee adaptee;
    
    public Adapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }
    
    @Override
    public void operation() {
        adaptee.spezifischeOperation();
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        Adaptee adaptee = new Adaptee();
        ZielSchnittstelle adapter = new Adapter(adaptee);
        adapter.operation(); // Ausgabe: "Spezifische Operation des Adaptee"
    }
}
```
