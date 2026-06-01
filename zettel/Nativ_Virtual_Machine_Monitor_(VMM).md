---
id: af63ebd2-9631-4cda-8820-9967fb31ec88
title: "Nativ Virtual Machine Monitor (VMM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - systemarchitektur
  - cloud-computing
  - hardware
  - isolation
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Nativ Virtual Machine Monitor (VMM)]]

- **Kernkonzept:** Ein [[Nativ Virtual Machine Monitor|Nativ-VMM]] ist eine [[Virtualisierungs|virtualisierende]] Software-Schicht, die direkt auf der [[Hardware]] läuft und [[Gastsystem|Gastsysteme]] mit minimalem [[Betriebssystem|Betriebssystemkern]] verwaltet, um [[Isolation]] und [[Ressourcenverwaltung]] zu ermöglichen.
- **Nutzen & Zweck:** Der [[Nativ-VMM]] löst das Problem der effizienten [[Hardware]]-Nutzung, indem er mehrere [[Gastsysteme]] parallel auf einer physischen Maschine betreibt, ohne dass diese sich gegenseitig beeinflussen. Dies ermöglicht [[Skalierbarkeit]], [[Sicherheit]] und [[Kostenreduktion]] in [[verteilten Systemen]] und [[Cloud-Computing]]-Umgebungen.
- **Abgrenzung & Grenzen:** Ein [[Nativ-VMM]] sollte nicht genutzt werden, wenn volle [[Betriebssystem]]-Funktionalität oder [[Anwendungs]]-Kompatibilität erforderlich ist, da er nur minimale [[Systemdienste]] bereitstellt. Im Gegensatz zu [[Hosted-VMMs]] delegiert er keine Aufgaben an ein vollwertiges [[Host-Betriebssystem]], was die [[Flexibilität]] einschränkt. Für [[Prozess-VMs]] (z. B. [[Java Virtual Machine|JVM]]) ist er ungeeignet, da diese auf [[Anwendungsebene]] arbeiten.
- **Beispiel / Code:** Ein typischer Einsatz eines [[Nativ-VMM]] ist die Bereitstellung von [[Infrastructure-as-a-Service|IaaS]] in der Cloud. Beispiel:
```
// Pseudocode: Starten einer VM auf einem Nativ-VMM (z. B. Xen)
vmm.create_vm(
    guest_os="Linux Kernel 5.4",
    cpu_cores=4,
    memory_gb=8,
    storage_gb=100
);
```
Hier läuft der [[VMM]] direkt auf der [[Hardware]] und verwaltet die [[Ressourcen]] der [[Gast-VM]] ohne Zwischenschicht eines [[Host-Betriebssystems]].
