---
id: fe670f57-7850-4580-9480-e3f5992bdb95
title: "Klassen-Adapter"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - adapter_variante
  - draft
source: "software_engineering_kapitel_15"
---

# [[Klassen-Adapter]]

- **Kernkonzept:** Der Klassen-Adapter ist ein strukturelles Entwurfsmuster, das eine bestehende Klasse durch Vererbung an eine Zielschnittstelle anpasst, um Inkompatibilitäten zwischen Schnittstellen zu überwinden. Dabei wird eine neue Adapterklasse erstellt, die von der zu adaptierenden Klasse erbt und die Zielschnittstelle implementiert.
- **Nutzen & Zweck:** Das Konzept existiert, um vorhandene Klassen oder Bibliotheken mit inkompatiblen Schnittstellen in ein bestehendes System zu integrieren, ohne deren Quellcode ändern zu müssen. Es löst das Problem, dass Klassen mit unterschiedlichen Schnittstellen nicht direkt zusammenarbeiten können, indem es eine vermittelnde Schicht einführt, die die Kommunikation ermöglicht. Besonders nützlich ist es, wenn eine Klasse wiederverwendet werden soll, deren Schnittstelle nicht der benötigten entspricht.
- **Abgrenzung & Grenzen:** Der Klassen-Adapter sollte nicht genutzt werden, wenn die anzupassende Klasse oder deren Unterklassen nicht durch Vererbung erweitert werden können, beispielsweise bei finalen Klassen. Zudem ist er ungeeignet, wenn mehrere Klassen mit unterschiedlichen Schnittstellen angepasst werden müssen, da für jede Klasse ein separater Adapter erforderlich wäre. Im Vergleich zum Objekt-Adapter ist der Klassen-Adapter weniger flexibel, da er keine Unterklassen der adaptierten Klasse unterstützt und Änderungen an der adaptierten Klasse direkt auf den Adapter durchschlagen. Der Objekt-Adapter ist hier vorzuziehen, da er Komposition statt Vererbung nutzt.
- **Beispiel / Code:** ```java
// Zielschnittstelle, die vom Client erwartet wird
interface ZielSchnittstelle {
    void operation();
}

// Bestehende Klasse mit inkompatibler Schnittstelle
class Adaptee {
    void spezifischeOperation() {
        System.out.println("Spezifische Operation ausgeführt");
    }
}

// Klassen-Adapter, der Adaptee an ZielSchnittstelle anpasst
class KlassenAdapter extends Adaptee implements ZielSchnittstelle {
    @Override
    public void operation() {
        spezifischeOperation(); // Aufruf der adaptierten Methode
    }
}

// Nutzung im Client-Code
public class Client {
    public static void main(String[] args) {
        ZielSchnittstelle adapter = new KlassenAdapter();
        adapter.operation(); // Ausgabe: "Spezifische Operation ausgeführt"
    }
}
```
