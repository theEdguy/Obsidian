---
id: 05f4a0c8-b25a-40b3-928e-9795ab8021a6
title: "Join"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_08"
---

# [[Join]]

- **Kernkonzept:** Ein 'Join' in UML-Aktivitätsdiagrammen ist ein Kontrollknoten, der mehrere parallele Abläufe (Token) synchronisiert und zu einem einzigen Ablauf zusammenführt. Er stellt sicher, dass alle eingehenden Transitionen abgeschlossen sind, bevor der Ablauf fortgesetzt wird.
- **Nutzen & Zweck:** Der 'Join' existiert, um parallele Prozesse oder Threads in einem System zu koordinieren und sicherzustellen, dass abhängige Aktionen erst ausgeführt werden, wenn alle vorherigen parallelen Schritte abgeschlossen sind. Dies löst das Problem der Synchronisation und verhindert Race Conditions oder inkonsistente Zustände in komplexen Abläufen.
- **Abgrenzung & Grenzen:** Ein 'Join' sollte nicht genutzt werden, wenn keine parallelen Abläufe synchronisiert werden müssen oder wenn die Reihenfolge der Ausführung irrelevant ist. Im Gegensatz zu einem 'Merge'-Knoten, der alternative Pfade zusammenführt, synchronisiert ein 'Join' ausschließlich parallele Pfade. Bei einfachen sequenziellen Abläufen ist ein 'Join' überflüssig und erhöht unnötig die Komplexität des Diagramms.
- **Beispiel / Code:** ```java
// Beispiel für parallele Threads, die mit einem Join synchronisiert werden
Thread thread1 = new Thread(() -> {
    System.out.println("Thread 1 ausgeführt");
});

Thread thread2 = new Thread(() -> {
    System.out.println("Thread 2 ausgeführt");
});

thread1.start();
thread2.start();

try {
    thread1.join(); // Wartet auf Abschluss von Thread 1
    thread2.join(); // Wartet auf Abschluss von Thread 2
} catch (InterruptedException e) {
    e.printStackTrace();
}

System.out.println("Beide Threads abgeschlossen - Join-Punkt");
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a4
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
