---
id: 8b2b44b5-4e23-4e3b-9e86-a6ccdd8b1b20
title: "Threads"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - parallelität
  - betriebssysteme
  - verteilte-systeme
  - kontextwechsel
  - multithreading
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Threads]]

- **Kernkonzept:** Ein [[Thread|Thread]] ist ein leichtgewichtiger [[Prozess|Prozess]], der als minimaler Software-[[Prozessor]] innerhalb eines [[Prozess|Prozesses]] ausgeführt wird. [[Thread|Threads]] teilen sich den gleichen [[Adressraum]] und ermöglichen parallele Ausführung von [[Instruktion|Instruktionen]] im selben [[Kontext]].
- **Nutzen & Zweck:** [[Thread|Threads]] lösen das Problem der Blockierung bei [[E/A-Operation|E/A-Operationen]] und ermöglichen effiziente Nutzung von [[Multicore-Prozessor|Multicore-Prozessoren]] durch Parallelität. Sie reduzieren den Overhead im Vergleich zu [[Prozess|Prozessen]] und vereinfachen die Strukturierung komplexer Anwendungen, insbesondere in [[Verteilte Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** [[Thread|Threads]] sollten nicht genutzt werden, wenn starke Isolation zwischen Ausführungseinheiten erforderlich ist, da sie sich einen [[Adressraum]] teilen und fehleranfälliger gegenüber [[Race Condition|Race Conditions]] sind. Alternativen wie [[Prozess|Prozesse]] bieten mehr Sicherheit, sind aber teurer in der Erstellung und beim [[Kontextwechsel]]. [[User-Level-Thread|User-Level-Threads]] sind effizient, blockieren jedoch den gesamten [[Prozess]], wenn ein [[Thread]] blockiert.
- **Beispiel / Code:** ```java
// Beispiel: Multithreaded Server in Java
class WorkerThread extends Thread {
    public void run() {
        // Blockierende E/A-Operation (z. B. Datei lesen)
        System.out.println("Thread " + Thread.currentThread().getId() + " verarbeitet Request");
    }
}

public class Server {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            new WorkerThread().start(); // Startet parallele Threads
        }
    }
}
```
