---
id: 66b79b36-3148-4466-8279-edc9f4aa59fd
title: "Starke Mobilität"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - mobilitaet
  - agentensysteme
  - lastverteilung
  - heterogene_systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Starke Mobilität]]

- **Kernkonzept:** Starke Mobilität bezeichnet die Fähigkeit, ein [[Prozess|Prozesses]] oder [[Agent|Agenten]] inklusive seines [[Ausführungszustand|Ausführungszustands]] und [[Daten-Segment|Daten-Segments]] zwischen [[Knoten|Knoten]] in einem [[Verteiltes System|verteilten System]] zu migrieren, ohne die [[Ausführung]] zu unterbrechen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Lastverteilung]], [[Fehlertoleranz]] und [[Dynamische Anpassung|dynamischen Anpassung]] in [[Verteilte Systeme|verteilten Systemen]], indem es ermöglicht, [[Prozess|Prozesse]] oder [[Agent|Agenten]] nahtlos zwischen [[Knoten]] zu verschieben, ohne deren [[Ausführungskontext]] zu verlieren. Dies ist besonders nützlich für [[Echtzeitanwendungen]] oder Systeme mit hohen [[Verfügbarkeitsanforderungen]].
- **Abgrenzung & Grenzen:** Starke Mobilität sollte nicht genutzt werden, wenn die [[Komplexität]] der Implementierung (z. B. durch heterogene [[Hardware]] oder [[Betriebssystem|Betriebssysteme]]) den Nutzen übersteigt. Im Gegensatz zur [[Schwache Mobilität|schwachen Mobilität]] erfordert sie eine [[Abstrakte Maschine|abstrakte Maschine]] (z. B. [[Java Virtual Machine|JVM]]) oder interpretierte [[Programmiersprache|Programmiersprachen]], um den [[Ausführungszustand]] portabel zu halten. Für einfache [[Code Migration|Code-Migrationen]] (z. B. [[Code-on-Demand]]) ist schwache Mobilität oft ausreichend.
- **Beispiel / Code:** Ein Beispiel für starke Mobilität ist ein [[Mobiler Agent|mobiler Agent]] in Java, der seinen [[Ausführungszustand]] (z. B. Stack, Programmzähler) serialisiert und auf einen anderen [[Knoten]] migriert:

```java
// Pseudocode für einen mobilen Agenten
class MobileAgent implements Serializable {
    private int state; // Daten-Segment
    private transient Thread executionThread; // Ausführungszustand (muss serialisierbar gemacht werden)
    
    void migrateTo(Node target) {
        // Serialisiere Agent inkl. Ausführungszustand
        byte[] serializedAgent = serialize(this);
        target.receive(serializedAgent);
        // Deserialisiere und setze Ausführung fort
    }
}
```

Hinweis: Die tatsächliche Implementierung erfordert eine [[Virtual Machine|VM]] (z. B. JVM) oder spezielle Bibliotheken, um den [[Thread-Kontext]] zu erfassen.
