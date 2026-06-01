---
id: e7759ac1-f5e8-4441-aaa0-341ee84391d0
title: "Mobile Agents (MA)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - autonomie
  - mobilität
  - heterogene_systeme
  - netzwerk
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Mobile Agents (MA)]]

- **Kernkonzept:** Mobile [[Agent|Agenten]] sind autonome Programme, die sich in einem [[Verteiltes System|verteilten System]] bewegen und dabei ihren [[Ausführungszustand]] sowie [[Code]] und [[Daten]] mitführen, um Aufgaben dezentral zu erledigen.
- **Nutzen & Zweck:** Sie lösen Probleme wie Netzwerklatenz, Bandbreitenbegrenzung oder dynamische Anpassung an [[Ressource|Ressourcen]], indem sie [[Berechnung|Berechnungen]] nahe an die Datenquellen verlagern. Besonders nützlich in heterogenen oder instabilen Netzwerken, wo [[Client-Server-Modell|Client-Server-Architekturen]] ineffizient sind.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache, statische Aufgaben oder Systeme mit homogenen [[Plattform|Plattformen]], da der Overhead für Migration und [[Sicherheit]] hoch ist. Unterscheidet sich von [[Code-on-Demand (CoD)|Code-on-Demand]] durch die Mitnahme des [[Ausführungszustand|Ausführungszustands]] und von [[Remote Procedure Call (RPC)|RPC]] durch die autonome Beweglichkeit. In heterogenen Systemen erfordert starke Mobilität eine [[Virtuelle Maschine|virtuelle Maschine]].
- **Beispiel / Code:** Ein mobiler Agent in Java (vereinfacht):
```java
public class DataCollectorAgent implements Agent {
    private String targetServer;
    private List<String> collectedData;
    
    public void run() {
        migrateTo(targetServer);  // Agent bewegt sich zum Zielknoten
        collectedData = queryLocalDatabase();
        processData();
        migrateBack();  // Rückkehr mit Ergebnissen
    }
}
```
Der Agent führt lokal auf dem Zielknoten [[Datenbankabfrage|Datenbankabfragen]] durch und kehrt mit den Ergebnissen zurück, ohne dass der [[Client]] dauerhaft verbunden sein muss.
