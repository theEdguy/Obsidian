---
id: 4ea8b7e7-2c6d-4c6b-8200-319d573afa07
title: "Multithreading"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - parallelisierung
  - verteilte-systeme
  - kontextwechsel
  - betriebssysteme
  - skalierbarkeit
  - server-architektur
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Multithreading]]

- **Kernkonzept:** Multithreading ermöglicht die parallele Ausführung mehrerer [[Thread|Threads]] innerhalb eines [[Prozess|Prozesses]], indem virtuelle [[Prozessor|Prozessoren]] genutzt werden, die sich einen gemeinsamen Adressraum teilen. Dies erlaubt effiziente [[Kontextwechsel|Kontextwechsel]] und [[Parallelisierung|Parallelverarbeitung]] von [[Instruktion|Instruktionen]] ohne teure [[Prozesswechsel|Prozesswechsel]].
- **Nutzen & Zweck:** Multithreading löst das Problem der [[Blockierung]] bei [[E/A-Operation|E/A-Operationen]] und ermöglicht die Nutzung von [[Multicore-Prozessor|Multicore-Prozessoren]] für echte [[Parallelität]]. Es reduziert [[Latenz]] in verteilten Systemen, vereinfacht die [[Strukturierung]] komplexer Anwendungen und verbessert die [[Skalierbarkeit]] von [[Server|Servern]] durch effiziente Ressourcennutzung.
- **Abgrenzung & Grenzen:** Multithreading sollte nicht genutzt werden, wenn [[Sicherheit]] oder [[Isolation]] kritisch sind, da [[Threads]] denselben Adressraum teilen und Fehleranfälliger für [[Race-Condition|Race-Conditions]] sind. Alternativen wie [[Prozess|Prozesse]] bieten bessere [[Fehlerisolation]], sind aber teurer in [[Erzeugung]] und [[Kontextwechsel]]. Bei einfachen Aufgaben kann ein [[Single-Thread|Single-Threaded]]-Ansatz oder ein [[Endlicher-Automat|endlicher Automat]] ausreichen.
- **Beispiel / Code:** ```java
// Beispiel: Multithreaded Server mit Dispatcher/Worker-Modell
ExecutorService executor = Executors.newFixedThreadPool(10);
ServerSocket serverSocket = new ServerSocket(8080);

while (true) {
    Socket clientSocket = serverSocket.accept();
    executor.submit(() -> {
        // Worker-Thread verarbeitet Request
        handleRequest(clientSocket);
    });
}
```

*Erläuterung*: Der Dispatcher-Thread nimmt [[Request|Requests]] entgegen und verteilt sie an Worker-Threads, die blockierende Operationen (z. B. [[E/A-Operation|E/A-Operationen]]) parallel abarbeiten.
