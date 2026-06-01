---
id: 258aa51a-0c64-4ec4-9099-31c4c2fdee0e
title: "Prinzip der Virtualisierung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - abstraktion
  - cloud_computing
  - ressourcenmanagement
  - isolation
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Prinzip der Virtualisierung]]

- **Kernkonzept:** Das Prinzip der Virtualisierung ermöglicht die Abstraktion von physischer [[Hardware|Hardware]] durch eine logische Schicht, die [[Ressource|Ressourcen]] wie Prozessoren, Speicher oder Netzwerke als virtuelle [[Instanz|Instanzen]] bereitstellt. Dies schafft isolierte und flexible [[Umgebung|Umgebungen]] für [[Anwendung|Anwendungen]] oder [[Betriebssystem|Betriebssysteme]].
- **Nutzen & Zweck:** Virtualisierung löst das Problem der ineffizienten [[Nutzung|Nutzung]] physischer [[Ressource|Ressourcen]] und ermöglicht die Konsolidierung mehrerer [[System|Systeme]] auf einer [[Hardware|Hardware]]. Sie bietet [[Isolation|Isolation]] für Sicherheit und Stabilität, vereinfacht die [[Bereitstellung|Bereitstellung]] von [[Dienst|Diensten]] und unterstützt [[Skalierbarkeit|Skalierbarkeit]] in verteilten [[System|Systemen]], z. B. im [[Cloud Computing|Cloud-Computing]].
- **Abgrenzung & Grenzen:** Virtualisierung sollte nicht genutzt werden, wenn Echtzeitanforderungen oder direkte [[Hardware|Hardware]]-Zugriffe (z. B. für Hochleistungsrechnen) kritisch sind, da die zusätzliche Abstraktionsschicht [[Latenz|Latenz]] oder [[Overhead|Overhead]] verursacht. Alternativen wie Container (z. B. Docker) bieten geringeren [[Overhead|Overhead]], aber weniger [[Isolation|Isolation]]. Bei einfachen [[Anwendung|Anwendungen]] ohne [[Ressource|Ressourcen]]-Konflikte ist Virtualisierung oft unnötig.
- **Beispiel / Code:** Ein Beispiel für eine Prozess-VM (Typ (a)) ist die Java Virtual Machine (JVM):
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Virtualized World!");
    }
}
```
Der [[Code|Code]] wird in Bytecode kompiliert und läuft isoliert in der JVM, unabhängig vom darunterliegenden [[Betriebssystem|Betriebssystem]] oder der [[Hardware|Hardware]].
