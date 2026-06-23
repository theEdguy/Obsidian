---
id: b58a91eb-cf7f-450b-a5e4-ac4fa9129936
title: "Brücke"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - strukturmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[Brücke]]

- **Kernkonzept:** Das Brückenmuster (Bridge) ist ein Strukturmuster, das die Abstraktion einer Funktionalität von ihrer Implementierung entkoppelt. Dadurch können beide unabhängig voneinander erweitert oder verändert werden, ohne sich gegenseitig zu beeinflussen.
- **Nutzen & Zweck:** Das Brückenmuster löst das Problem, dass Abstraktionen und ihre Implementierungen oft eng miteinander verknüpft sind, was zu starren Systemen führt. Es ermöglicht die unabhängige Weiterentwicklung von Schnittstellen und Implementierungen, erhöht die Flexibilität und erleichtert die Wartung. Besonders nützlich ist es, wenn mehrere Implementierungsvarianten für eine Abstraktion existieren oder wenn Änderungen an der Implementierung keine Auswirkungen auf den Client-Code haben sollen.
- **Abgrenzung & Grenzen:** Das Brückenmuster sollte nicht eingesetzt werden, wenn die Abstraktion und Implementierung stabil sind und keine unabhängige Variation erforderlich ist, da der zusätzliche Aufwand für die Entkopplung dann unnötig ist. Im Vergleich zum Adaptermuster, das bestehende inkompatible Schnittstellen verbindet, dient das Brückenmuster der präventiven Entkopplung von Abstraktion und Implementierung. Es ist komplexer als einfache Vererbung und sollte nur genutzt werden, wenn die Vorteile der Entkopplung tatsächlich benötigt werden.
- **Beispiel / Code:** ```java
// Abstraktion
abstract class Abstraktion {
    protected Implementierung implementierung;

    public Abstraktion(Implementierung impl) {
        this.implementierung = impl;
    }

    public abstract void operation();
}

// Implementierung
interface Implementierung {
    void operationImpl();
}

// Konkrete Implementierung A
class KonkreteImplA implements Implementierung {
    public void operationImpl() {
        System.out.println("Konkrete Implementierung A");
    }
}

// Verfeinerte Abstraktion
class VerfeinerteAbstraktion extends Abstraktion {
    public VerfeinerteAbstraktion(Implementierung impl) {
        super(impl);
    }

    public void operation() {
        implementierung.operationImpl();
    }
}

// Nutzung
public class Main {
    public static void main(String[] args) {
        Implementierung implA = new KonkreteImplA();
        Abstraktion abstraktion = new VerfeinerteAbstraktion(implA);
        abstraktion.operation();
    }
}
```
