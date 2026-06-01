---
id: b60f8efe-ccf5-400c-bd6f-90214a6cbf87
title: "Daten-Segment"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - code-migration
  - zustandsverwaltung
  - mobilitaet
  - serialisierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Daten-Segment]]

- **Kernkonzept:** Das Daten-Segment ist ein Bestandteil einer migrierbaren [[Komponente|Komponenten]], das den aktuellen [[Zustand|Zustände]] der [[Variable|Variablen]] und [[Datenstruktur|Datenstrukturen]] speichert, während das [[Code-Segment]] die ausführbaren Anweisungen enthält.
- **Nutzen & Zweck:** Es ermöglicht die [[Wiederherstellung]] des [[Ausführungszustand|Ausführungszustandes]] nach einer [[Migration]] in [[Verteilte Systeme|verteilten Systemen]], insbesondere bei [[schwache Mobilität|schwacher Mobilität]], wo nur Code und Daten übertragen werden. Dadurch bleibt der [[Kontext]] erhalten, ohne den [[Thread]]-Zustand mitführen zu müssen.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[starke Mobilität]], da hier der [[Ausführungszustand]] (z. B. Stack, Register) zusätzlich migriert werden muss. In [[heterogene Systeme|heterogenen Systemen]] kann die [[Portabilität]] eingeschränkt sein, wenn das Daten-Segment plattformabhängige Formate verwendet. Alternativen wie [[Serialisierung]] oder [[abstrakte Maschinen]] (z. B. JVM) sind oft notwendig.
- **Beispiel / Code:** In Java könnte ein Daten-Segment als serialisiertes Objekt dargestellt werden:
```java
class MobileComponent implements Serializable {
    private int counter;  // Daten-Segment
    private String state;
    
    public void execute() {  // Code-Segment
        counter++;
    }
}
```
Bei Migration wird nur das serialisierte Objekt (Daten-Segment) übertragen, nicht der Stack oder Programmzähler.
