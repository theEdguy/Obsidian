---
id: e7bd9544-4cca-402d-986a-f9d9204e27ac
title: "Cloning (von Objekten)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - mobilitaet
  - objektorientierung
  - fehlertoleranz
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Cloning (von Objekten)]]

- **Kernkonzept:** Beim Cloning wird ein [[Klon|Klone]] eines [[Objekt|Objekts]] erstellt und in denselben [[Ausführungszustand]] versetzt, um die [[starke Mobilität]] in [[Verteilte Systeme|verteilten Systemen]] zu ermöglichen. Dabei werden [[Code-Segment]], [[Daten-Segment]] und [[Ausführungszustand]] übertragen.
- **Nutzen & Zweck:** Cloning löst das Problem der [[Code Migration]] in [[heterogene Systeme|heterogenen Systemen]], indem es die [[Ausführung]] eines [[Objekt|Objekts]] auf einem anderen [[Knoten]] ermöglicht, ohne den ursprünglichen [[Prozess]] zu unterbrechen. Es unterstützt [[Lastverteilung]], [[Fehlertoleranz]] und [[Skalierbarkeit]].
- **Abgrenzung & Grenzen:** Cloning sollte nicht genutzt werden, wenn [[schwache Mobilität]] ausreicht, da es komplexer und ressourcenintensiver ist. Im Gegensatz zu [[Migration]] wird kein [[Objekt]] verschoben, sondern ein neuer [[Klon]] erstellt. In [[homogene Systeme|homogenen Systemen]] kann [[Migration]] effizienter sein. Bei [[interpretierte Sprachen|interpretierten Sprachen]] mit [[virtuelle Maschine|VMs]] ist Cloning einfacher umsetzbar als in nativen Umgebungen.
- **Beispiel / Code:** In Java könnte ein einfaches Cloning eines mobilen Agenten wie folgt aussehen:
```java
public class MobileAgent implements Serializable {
    private String state;
    private int executionPoint;

    public MobileAgent clone() {
        MobileAgent clone = new MobileAgent();
        clone.state = this.state;
        clone.executionPoint = this.executionPoint;
        return clone;
    }
    public void execute() {
        // Ausführungslogik, die den Zustand nutzt
    }
}
```
Hier wird der [[Ausführungszustand]] (z. B. `executionPoint`) zusammen mit dem [[Daten-Segment]] (z. B. `state`) kopiert, um den Klon nahtlos fortzusetzen.
