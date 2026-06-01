---
id: 0f40b41b-25d3-4f8e-bc00-bd2d166e655d
title: "Virtualisierung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - abstraktion
  - systemarchitektur
  - virtualisierung
  - ressourcenverwaltung
  - isolation
  - portierbarkeit
  - betriebssysteme
  - cloud-computing
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Virtualisierung]]

- **Kernkonzept:** Virtualisierung ermöglicht die Nachbildung von [[Hardware]]- oder [[Software]]-[[Schnittstelle|Schnittstellen]], um [[System|Systeme]], [[Betriebssystem|Betriebssysteme]] oder [[Anwendung|Anwendungen]] unabhängig von der physischen [[Implementierung]] auszuführen. Sie schafft eine [[Abstraktionsebene]], die [[Portierbarkeit]], [[Isolation]] und effiziente [[Ressourcen|Ressourcennutzung]] in [[Verteilte Systeme|verteilten Systemen]] verbessert.
- **Nutzen & Zweck:** Virtualisierung löst das Problem der schnellen [[Hardware]]-Evolution und ineffizienten [[Ressourcen|Ressourcennutzung]], indem sie [[Software]] von physischen [[Ressource|Ressourcen]] entkoppelt. Sie ermöglicht [[Migration]] von [[Code]], verbessert die [[Sicherheit]] durch [[Isolation]], vereinfacht die [[Verwaltung]] heterogener [[System|Systeme]] und unterstützt [[Skalierbarkeit]] sowie flexible Bereitstellung von [[Dienst|Diensten]], insbesondere im [[Cloud Computing]]. Durch die Abstraktionsebene wird die [[Portierbarkeit]] von [[Anwendung|Anwendungen]] über verschiedene [[Plattform|Plattformen]] hinweg gewährleistet.
- **Abgrenzung & Grenzen:** Virtualisierung sollte nicht genutzt werden, wenn maximale [[Performance]] oder direkte [[Hardware]]-Zugriffe erforderlich sind, da sie [[Overhead]] durch die [[Abstraktionsebene]] verursacht. Alternativen wie [[Containerisierung]] oder [[Bare-Metal]]-Ausführung können effizienter sein, wenn keine [[Isolation]] oder [[Portierbarkeit]] benötigt wird. Bei [[Echtzeit-System|Echtzeit-Systemen]] kann der [[Latenz|Latenz]]-Overhead problematisch sein, da harte [[Latenz|Latenzanforderungen]] nicht erfüllt werden können. Zudem ist Virtualisierung weniger geeignet für [[System|Systeme]] mit hoher Abhängigkeit von spezifischer [[Hardware]].
- **Beispiel / Code:** Virtualisierung kann auf verschiedenen Ebenen erfolgen. Ein Beispiel für Hardware-Virtualisierung ist die Nutzung einer virtuellen Maschine (VM) mit einem [[Hypervisor]]:

```bash
# Starten einer VM mit QEMU (Befehlszeile)
qemu-system-x86_64 -m 4G -enable-kvm -hda ubuntu.img
```

Hier wird ein [[Gastsystem]] (z. B. Ubuntu) auf einem [[Hostsystem]] ausgeführt, wobei die [[Hardware]]-[[Schnittstelle|Schnittstellen]] des Gasts durch den [[Hypervisor]] nachgebildet werden.

Ein weiteres Beispiel ist die Prozess-Virtualisierung durch eine [[Java Virtual Machine|JVM]], die als Interpreter für [[Bytecode]] agiert:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Virtualized World!");
    }
}
```

Die [[Java Virtual Machine|JVM]] virtualisiert die [[Hardware]]-Instruktionen für das Programm und ermöglicht so [[Plattform|Plattformunabhängigkeit]].
