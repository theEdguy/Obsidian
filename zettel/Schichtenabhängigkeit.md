---
aliases:
- Schichtenarchitektur
date: 2026-05-30
id: 24ba687f-d2a8-4e55-8114-d86dceca6f7e
source: SWE Slides (Folien 211-225)
tags:
- software_engineering
- architekturprinzip
- softwarearchitektur
- design_rule
- draft
title: Schichtenabhängigkeit
---

# [[Schichtenabhängigkeit]]

- **Kernkonzept:** [[Schichtenabhängigkeit]] definiert die Regeln für die [[Interaktion]] zwischen [[Schicht|Schichten]] in einer [[geschichteten_Architektur]]: Höhere [[Schicht|Schichten]] dürfen tiefere nutzen, aber nicht umgekehrt.
- **Nutzen & Zweck:** Sie verhindert zyklische [[Abhängigkeit|Abhängigkeiten]] und fördert die [[Modularität]] sowie [[Wartbarkeit]] des Systems.
- **Abgrenzung & Grenzen:** Kann zu [[Performance]]-Problemen führen, wenn Daten durch mehrere [[Schicht|Schichten]] gereicht werden müssen. In [[Mikroservice|Mikroservice-Architekturen]] ist die [[Schicht|Schichten]]-Trennung weniger streng.
- **Beispiel / Code:** ```java
// Regelkonform: Logikschicht nutzt Datenzugriffsschicht
public class BusinessLogic {
    private DatabaseLayer dbLayer;
    
    public void processData() {
        dbLayer.saveData();
    }
}

// Regelverstoß: Datenzugriffsschicht nutzt Logikschicht
public class DatabaseLayer {
    private BusinessLogic logic; // Verstoß gegen Schichtenabhängigkeit
}
```
