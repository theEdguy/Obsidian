---
id: b6314b15-ad52-49e7-9a7c-aebb4ea26d8a
title: "Prioritätsbasiertes Scheduling"
date: 2026-06-01
tags:
  - verteilte_systeme
  - scheduling
  - betriebssysteme
  - verteilte-systeme
  - prozessverwaltung
  - priorisierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Prioritätsbasiertes Scheduling]]

- **Kernkonzept:** Prioritätsbasiertes Scheduling ist ein [[Scheduling-Verfahren|Scheduling-Verfahren]], bei dem [[Prozess|Prozesse]] oder [[Thread|Threads]] basierend auf ihrer [[Priorität|Priorität]] ausgeführt werden, um kritische oder zeitkritische Aufgaben bevorzugt zu behandeln.
- **Nutzen & Zweck:** Es löst das Problem der effizienten Ressourcenzuweisung in [[System|Systemen]], insbesondere wenn [[Prozess|Prozesse]] mit unterschiedlichen Dringlichkeiten konkurrieren. Es ermöglicht die Unterbrechung laufender [[Prozess|Prozesse]] zugunsten höherpriorisierter Aufgaben, z. B. bei [[Out-of-Band-Kommunikation|Out-of-Band-Kommunikationen]] oder [[Echtzeitanwendung|Echtzeitanwendungen]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[System|Systeme]], in denen alle [[Prozess|Prozesse]] gleichberechtigt sind oder Fairness im Vordergrund steht. Im Vergleich zu [[Round-Robin-Scheduling|Round-Robin-Scheduling]] oder [[First-Come-First-Served|FCFS]] kann es zu [[Starvation|Starvation]] niedrigpriorisierter [[Prozess|Prozesse]] führen. Alternativen wie [[Multilevel-Feedback-Queue|Multilevel-Feedback-Queues]] kombinieren Prioritäten mit Fairness.
- **Beispiel / Code:** Ein einfaches Beispiel für prioritätsbasiertes Scheduling in einem [[Betriebssystem|Betriebssystem]]:
```c
struct process {
    int pid;
    int priority;
};

// Höhere Prioritätszahl = höhere Priorität
void schedule() {
    struct process *next_process = get_highest_priority_process();
    execute(next_process);
}
```
In [[verteilten Systemen|verteilten Systemen]] kann dies genutzt werden, um dringende [[Nachricht|Nachrichten]] (z. B. Unterbrechungen) vorrangig zu behandeln.
