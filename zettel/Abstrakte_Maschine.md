---
id: 7c82e3d7-500e-491e-a8b1-aa9416c7c619
title: "Abstrakte Maschine"
date: 2026-06-01
tags:
  - verteilte_systeme
  - code_migration
  - virtualisierung
  - portabilität
  - laufzeitumgebung
  - heterogene_systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Abstrakte Maschine]]

- **Kernkonzept:** Eine [[abstrakte Maschine|abstrakten Maschine]] definiert eine einheitliche Ausführungsumgebung für [[Programm|Programme]], unabhängig von der zugrundeliegenden Hardware oder dem [[Betriebssystem|Betriebssystemen]]. Sie ermöglicht die Ausführung von [[Code|Code]] in heterogenen [[System|Systemen]] durch Abstraktion der [[Prozessor|Prozessorkontexte]] und [[Laufzeitumgebung|Laufzeitumgebungen]].
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Code-Migration]] in heterogenen [[verteilten System|verteilten Systemen]], indem es [[Portabilität]] und [[Interoperabilität]] sicherstellt. Ohne eine [[abstrakte Maschine|abstrakte Maschine]] wäre die Migration von [[Prozess|Prozessen]] oder [[Thread|Threads]] zwischen unterschiedlichen [[Plattform|Plattformen]] aufgrund inkompatibler [[Hardware]]- und [[Software]]-Schnittstellen nicht möglich.
- **Abgrenzung & Grenzen:** Eine [[abstrakte Maschine|abstrakte Maschine]] sollte nicht genutzt werden, wenn maximale [[Performance]] oder direkte [[Hardware]]-Zugriffe erforderlich sind, da die zusätzliche Abstraktionsebene [[Overhead]] verursacht. Alternativen wie [[nativ kompilierter Code]] oder [[hardwarespezifische Optimierung|hardwarespezifische Optimierungen]] sind in solchen Fällen vorzuziehen. Zudem ist sie für [[Echtzeitsystem|Echtzeitsysteme]] oft ungeeignet, da die [[Laufzeitumgebung]] deterministisches Verhalten erschweren kann.
- **Beispiel / Code:** Ein klassisches Beispiel ist die Java Virtual Machine (JVM):
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hallo, Welt!");
    }
}
```
Der [[Bytecode]] dieses [[Programm|Programms]] wird von der JVM interpretiert oder just-in-time kompiliert, unabhängig davon, ob das [[System]] auf x86-, ARM- oder einer anderen [[Architektur]] läuft. Die JVM fungiert hier als [[abstrakte Maschine|abstrakte Maschine]].
