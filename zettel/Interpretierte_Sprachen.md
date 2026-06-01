---
id: 2d419282-f26a-4ec1-8ca8-6d6e6219d7ca
title: "Interpretierte Sprachen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - plattformunabhängigkeit
  - abstrakte_maschine
  - interpretation
  - heterogene_systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Interpretierte Sprachen]]

- **Kernkonzept:** Interpretierte [[Sprache|Sprachen]] führen [[Quelltext|Quelltexte]] nicht direkt auf der Hardware aus, sondern nutzen eine [[abstrakte Maschine]] (z. B. eine [[Virtuelle Maschine|VM]]), die den [[Code]] zur Laufzeit übersetzt und ausführt. Dies ermöglicht [[Plattformunabhängigkeit]] in [[heterogenen Systemen]] durch Abstraktion von Hardware- und Betriebssystemdetails.
- **Nutzen & Zweck:** Sie lösen das [[Problem]] der [[Code-Migration]] in [[verteilten Systemen]], indem sie [[Portabilität]] und [[starke Mobilität]] ermöglichen – insbesondere bei [[Migration]] von [[Prozess|Prozessen]] oder [[Thread|Threads]] mit [[Ausführungszustand]]. Durch die [[abstrakte Maschine]] entfällt die Notwendigkeit, [[Code]] für jede Zielplattform neu zu kompilieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Performance-kritische Anwendungen]], da die Interpretation zur Laufzeit langsamer ist als [[nativ kompilierter Code]]. Alternativen wie [[Ahead-of-Time-Kompilierung]] oder [[maschinenspezifische Optimierung]] bieten höhere Effizienz, verlieren aber [[Plattformunabhängigkeit]]. Zudem erfordern interpretierte [[Sprache|Sprachen]] oft eine [[Laufzeitumgebung]], was den Ressourcenbedarf erhöht.
- **Beispiel / Code:** Ein Java-Programm wird als Bytecode für die [[Java Virtual Machine]] (JVM) kompiliert:
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hallo, verteiltes System!");
    }
}
```
Der Bytecode läuft auf jeder Plattform mit JVM, ohne Neukompilierung. Bei [[Code-Migration]] (z. B. [[Mobile Agent|Mobile Agents]]) kann der [[Ausführungszustand]] inkl. Stack und Variablen serialisiert und auf einem anderen Knoten fortgesetzt werden.
