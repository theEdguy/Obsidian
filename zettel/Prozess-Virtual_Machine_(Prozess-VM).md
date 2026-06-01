---
id: 2063ac2d-1147-4dd6-8bcf-fd621426dfc8
title: "Prozess-Virtual Machine (Prozess-VM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - prozessmanagement
  - plattformunabhängigkeit
  - cloud-computing
  - emulation
  - isolierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Prozess-Virtual Machine (Prozess-VM)]]

- **Kernkonzept:** Eine Prozess-VM ist eine [[Virtualisierung|virtualisierte]] Umgebung, die einen einzelnen [[Prozess]] isoliert ausführt, indem sie [[Instruktion|Instruktionen]] interpretiert oder emuliert. Sie läuft als Anwendung auf einem [[Betriebssystem]] und ermöglicht die Ausführung von [[Programm|Programmen]] unabhängig von der zugrundeliegenden [[Hardware]].
- **Nutzen & Zweck:** Die Prozess-VM löst das Problem der [[Plattform|plattform]]unabhängigen Ausführung von [[Anwendung|Anwendungen]] und [[Bibliothek|Bibliotheken]]. Sie ermöglicht [[Portabilität]], [[Sicherheit]] durch Isolation und vereinfacht die Entwicklung, indem sie [[Abhängigkeit|Abhängigkeiten]] von der [[Hardware]] oder dem [[Betriebssystem]] reduziert. Häufig genutzt in [[Cloud Computing]] für [[Infrastructure-as-a-Service|IaaS]]-Dienste.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Low-Level]]-Operationen oder [[Hardware]]-nahe [[Programmierung]], da sie auf einem [[Interpreter]] oder [[Emulator]] basiert und somit [[Performance|performantere]] Alternativen wie [[Native Virtual Machine Monitor|native VMMs]] (Typ (b)) oder [[Hosted Virtual Machine Monitor|hosted VMMs]] (Typ (c)) unterlegen ist. Letztere virtualisieren die gesamte [[Hardware]] und ermöglichen die Ausführung vollständiger [[Betriebssystem|Betriebssysteme]]. Prozess-VMs bieten keine vollständige [[Isolation]] wie [[System-VM|System-VMs]].
- **Beispiel / Code:** Ein klassisches Beispiel ist die Java Virtual Machine (JVM):
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hallo, Welt!");
    }
}
```
Der [[Bytecode]] wird von der JVM interpretiert oder just-in-time kompiliert, unabhängig vom zugrundeliegenden [[Betriebssystem]] oder der [[Hardware]].
