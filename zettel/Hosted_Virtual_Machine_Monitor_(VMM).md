---
id: f3230661-7e32-456f-8284-69aadffe5c81
title: "Hosted Virtual Machine Monitor (VMM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - betriebssysteme
  - cloud-computing
  - infrastruktur
  - isolation
  - hypervisor
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Hosted Virtual Machine Monitor (VMM)]]

- **Kernkonzept:** Ein [[Hosted Virtual Machine Monitor|Hosted VMM]] ist eine [[Virtualisierungslösung|Virtualisierungslösung]], die als Anwendung auf einem bestehenden [[Betriebssystem]] läuft und [[Gastsysteme|Gastsysteme]] in virtuellen [[Maschinen]] ausführt. Im Gegensatz zu nativen VMMs nutzt es die [[Dienste]] des [[Wirtsbetriebssystems]] für Hardware-Zugriffe.
- **Nutzen & Zweck:** Der [[Hosted VMM]] ermöglicht die [[Ausführung]] mehrerer [[Betriebssysteme]] auf einer einzigen physischen [[Hardware]], ohne ein dediziertes [[Host-System]] zu benötigen. Dies löst [[Probleme]] der [[Hardware-Auslastung]], [[Isolation]] von [[Anwendungen]] und [[Kompatibilität]] mit bestehender Software. Besonders nützlich in [[Cloud-Computing]]-Umgebungen für [[Infrastructure-as-a-Service]] ([[IaaS]]).
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Szenarien]], die maximale [[Performance]] oder direkte [[Hardware-Kontrolle]] erfordern, da der [[Overhead]] des [[Wirtsbetriebssystems]] die [[Effizienz]] reduziert. Unterscheidet sich von [[nativen VMMs]] (z. B. [[Hypervisor]] Typ 1), die direkt auf der [[Hardware]] laufen, und [[Prozess-VMs]] (z. B. [[Java Virtual Machine]]), die nur einzelne [[Anwendungen]] virtualisieren. Weniger [[Isolation]] als native VMMs, aber einfacher zu [[installieren]] und zu [[verwalten]].
- **Beispiel / Code:** Ein typisches Beispiel ist die Nutzung von **VirtualBox** oder **VMware Workstation** auf einem Linux- oder Windows-[[Host-System]]:

```bash
# Starten einer virtuellen Maschine mit VirtualBox (CLI)
VBoxManage startvm "Ubuntu-Gast" --type headless
```

Hier läuft der VMM als Anwendung auf dem [[Wirtsbetriebssystem]], während das [[Gastsystem]] (z. B. Ubuntu) in einer isolierten Umgebung ausgeführt wird. Der VMM delegiert Hardware-Anfragen (z. B. Netzwerk, Festplatte) an das [[Wirtsbetriebssystem]].
