---
id: 2f43a67d-7972-4249-9686-f827780b9908
title: "Virtuelle Maschine (VM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - code_migration
  - plattformunabhängigkeit
  - abstrakte_maschine
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Virtuelle Maschine (VM)]]

- **Kernkonzept:** Eine [[Virtuelle Maschine|Virtuelle Maschine]] (VM) ist eine Software-Implementierung einer [[Abstrakte Maschine|abstrakten Maschine]], die [[Code]] in einer isolierten Umgebung ausführt und dabei Hardware- und Betriebssystemabhängigkeiten abstrahiert.
- **Nutzen & Zweck:** VMs lösen das Problem der [[Heterogenität]] in [[Verteilte Systeme|verteilten Systemen]], indem sie eine einheitliche [[Ausführungsumgebung]] für [[Code]] bereitstellen. Sie ermöglichen [[Code-Migration]] und [[Portabilität]] über verschiedene [[Plattform|Plattformen]] hinweg, ohne Anpassungen am [[Quellcode]] vornehmen zu müssen.
- **Abgrenzung & Grenzen:** VMs sollten nicht genutzt werden, wenn maximale [[Performance]] oder direkte Hardwarezugriffe erforderlich sind, da die zusätzliche Abstraktionsschicht [[Overhead]] verursacht. Alternativen wie [[Container]] oder native [[Kompilierung]] sind in solchen Fällen effizienter. Zudem sind VMs nicht für [[Echtzeit-Systeme]] geeignet, da die [[Latenz]] durch die [[Interpretation]] oder [[Just-in-Time-Kompilierung]] erhöht wird.
- **Beispiel / Code:** Ein einfaches Beispiel in Java, das die Plattformunabhängigkeit einer VM demonstriert:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Diese Anwendung läuft auf jeder Plattform mit einer Java-VM.");
    }
}
```

Die Java-VM (JVM) interpretiert den [[Bytecode]] und führt ihn auf jedem unterstützten [[Betriebssystem]] aus, ohne dass der [[Quellcode]] angepasst werden muss.
