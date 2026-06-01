---
id: 632aed06-b056-4430-8cf2-309920452330
title: "Parallelität"
date: 2026-06-01
tags:
  - verteilte_systeme
  - software_engineering
  - architektur
  - performance
  - prozesse
  - threads
  - verteilte-systeme
  - parallelverarbeitung
  - kontextwechsel
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Parallelität]]

- **Kernkonzept:** [[Parallelität]] beschreibt die Fähigkeit eines [[System|Systems]], mehrere [[Berechnung|Berechnungen]], [[Prozess|Prozesse]] oder [[Thread|Threads]] gleichzeitig auszuführen, um die [[Performance]] zu steigern und [[Ressource|Ressourcen]] effizient zu nutzen. Sie wird durch die Nutzung von [[Multicore-Prozessor|Multicore-Prozessoren]] oder [[Verteilte Systeme|verteilten Systemen]] ermöglicht und ist essenziell für [[Echtzeitsystem|Echtzeitsysteme]] sowie hochperformante [[Anwendung|Anwendungen]].
- **Nutzen & Zweck:** [[Parallelität]] ermöglicht die gleichzeitige Bearbeitung mehrerer [[Aufgabe|Aufgaben]], verbessert die [[Skalierbarkeit]] und [[Reaktionszeit]] von [[System|Systemen]] und löst [[Blockierung|Blockierungen]] bei [[Ein-/Ausgabe-Operation|Ein-/Ausgabe-Operationen]]. Sie ist besonders wertvoll in [[Verteilte Systeme|verteilten Systemen]], wo sie die [[Netzwerklatenz]] verdeckt und die [[Durchsatzrate]] erhöht. Durch die effiziente Nutzung von [[Multicore-Prozessor|Multicore-Prozessoren]] wird die [[Antwortzeit]] optimiert, was für [[Echtzeitsystem|Echtzeitsysteme]] und leistungskritische [[Anwendung|Anwendungen]] entscheidend ist.
- **Abgrenzung & Grenzen:** [[Parallelität]] ist kein Ersatz für [[Nebenläufigkeit]], die sich auf die Verwaltung und Koordination von [[Prozess|Prozessen]] und [[Thread|Threads]] konzentriert. Sie erfordert spezifische [[Hardware]]-Unterstützung, wie [[Multicore-Prozessor|Multicore-Prozessoren]], und erhöht im Vergleich zur [[Sequenzielle_Abarbeitung|sequenziellen Abarbeitung]] die Komplexität des [[System|Systems]]. [[Parallelität]] sollte vermieden werden, wenn [[Aufgabe|Aufgaben]] stark voneinander abhängig sind oder der [[Overhead]] für [[Kontextwechsel]] die Leistungsvorteile überwiegt. Typische Herausforderungen sind [[Race Condition|Race Conditions]] und [[Deadlock|Deadlocks]], die durch sorgfältiges [[Synchronisation|Synchronisationsmanagement]] adressiert werden müssen.
- **Beispiel / Code:** ```java
// Beispiel für Parallelität in Java (ExecutorService)
ExecutorService executor = Executors.newFixedThreadPool(4);
for (int i = 0; i < 10; i++) {
    executor.submit(() -> {
        // Aufgabe parallel ausführen
    });
}
executor.shutdown();

// Beispiel: Multithreaded-Webserver zur parallelen Bearbeitung von Client-Anfragen
new Thread(() -> {
    try {
        handleRequest(clientSocket);
    } catch (IOException e) {
        e.printStackTrace();
    }
}).start();
```
Durch die Verteilung der [[Request|Requests]] auf mehrere [[Thread|Threads]] wird die [[Netzwerklatenz]] verdeckt und die [[Durchsatzrate]] des [[System|Systems]] signifikant erhöht.
