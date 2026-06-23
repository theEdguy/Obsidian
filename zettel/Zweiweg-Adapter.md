---
id: b1cfbc18-65c2-4d90-ba4d-047ce1f27445
title: "Zweiweg-Adapter"
date: 2026-06-24
tags:
  - software_engineering
  - design_pattern
  - adapter_variante
  - draft
source: "software_engineering_kapitel_15"
---

# [[Zweiweg-Adapter]]

- **Kernkonzept:** Der Zweiweg-Adapter ist eine spezielle Variante des Adapter-Designmusters, die zwei inkompatible Schnittstellen bidirektional miteinander verbindet. Er ermöglicht die Kommunikation zwischen Klassen, indem er sowohl die Schnittstelle der Zielklasse als auch die der adaptierten Klasse (Adaptee) anbietet und somit beide Richtungen der Interaktion unterstützt.
- **Nutzen & Zweck:** Der Zweiweg-Adapter existiert, um die Transparenz und Flexibilität in Systemen zu erhöhen, in denen Klassen mit unterschiedlichen Schnittstellen zusammenarbeiten müssen, ohne dass eine der beiden Schnittstellen verändert oder bevorzugt wird. Er löst das Problem, dass bestehende Bibliotheken oder Komponenten mit festen Schnittstellen in beide Richtungen integriert werden sollen, ohne die ursprüngliche Implementierung anpassen zu müssen. Dies ist besonders nützlich, wenn beide Schnittstellen für verschiedene Teile des Systems relevant sind und eine einseitige Anpassung zu Einschränkungen führen würde.
- **Abgrenzung & Grenzen:** Der Zweiweg-Adapter sollte nicht genutzt werden, wenn eine einfache, unidirektionale Anpassung ausreicht, da er durch die Bereitstellung beider Schnittstellen die Komplexität erhöht. Im Vergleich zum klassischen Adapter oder Objekt-Adapter ist er weniger verbreitet und kann zu unnötiger Verwirrung führen, wenn die bidirektionale Kommunikation nicht zwingend erforderlich ist. Zudem ist er ungeeignet, wenn die Schnittstellen stark voneinander abweichen oder wenn die Implementierung der adaptierten Klasse nicht erweitert oder überschrieben werden kann. In solchen Fällen sind einfachere Adapter-Varianten oder eine Neugestaltung der Schnittstellen vorzuziehen.
- **Beispiel / Code:** ```java
// Beispiel für einen Zweiweg-Adapter, der sowohl die Schnittstelle von X als auch von Y anbietet
public class TwoWayAdapter implements X, Y {
    private Adaptee adaptee;
    private Target target;

    public TwoWayAdapter(Adaptee adaptee, Target target) {
        this.adaptee = adaptee;
        this.target = target;
    }

    // Methoden der Schnittstelle X
    @Override
    public void methodX() {
        adaptee.methodY(); // Anpassung der Methode von Y an X
    }

    // Methoden der Schnittstelle Y
    @Override
    public void methodY() {
        target.methodX(); // Anpassung der Methode von X an Y
    }
}
```
