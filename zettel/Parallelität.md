---
id: 418935a0-42f6-43b3-9a2b-8c2872299158
title: "Parallelität"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - performance
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Parallelität]]

- **Kernkonzept:** [[Parallelität]] beschreibt die Fähigkeit eines Systems, mehrere [[Prozess|Prozesse]] oder [[Thread|Threads]] gleichzeitig auszuführen. Sie wird genutzt, um die [[Performance]] zu steigern und [[Ressource|Ressourcen]] effizient zu nutzen.
- **Nutzen & Zweck:** Sie ermöglicht die gleichzeitige Bearbeitung mehrerer Aufgaben und verbessert die [[Skalierbarkeit]] und [[Reaktionszeit]] des Systems. [[Parallelität]] ist essenziell für [[Echtzeitsystem|Echtzeitsysteme]] und hochperformante Anwendungen.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Nebenläufigkeit]] (Concurrency), die sich auf die Verwaltung von [[Prozess|Prozessen]] konzentriert. [[Parallelität]] erfordert Hardware-Unterstützung (z. B. Mehrkernprozessoren). Im Gegensatz zu [[Sequenzielle_Abarbeitung|sequenzieller Abarbeitung]] erhöht sie die Komplexität.
- **Beispiel / Code:** ```java
// Beispiel für Parallelität in Java (ExecutorService)
ExecutorService executor = Executors.newFixedThreadPool(4);
for (int i = 0; i < 10; i++) {
    executor.submit(() -> {
        // Aufgabe parallel ausführen
    });
}
executor.shutdown();
```
