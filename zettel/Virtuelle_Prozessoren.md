---
id: 1398e740-a41b-420f-bdf8-9160101a7198
title: "Virtuelle Prozessoren"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - virtualisierung
  - verteilte-systeme
  - parallelisierung
  - kontextwechsel
  - betriebssysteme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Virtuelle Prozessoren]]

- **Kernkonzept:** Virtuelle [[Prozessor|Prozessoren]] sind Software-basierte Abstraktionen physikalischer [[Prozessor|Prozessoren]], die als [[Thread|Threads]] oder [[Prozess|Prozesse]] die Ausführung von Instruktionsgruppen in einem definierten Kontext ermöglichen. Sie erlauben die Parallelisierung und effiziente Nutzung von Ressourcen in [[Verteiltes System|verteilten Systemen]].
- **Nutzen & Zweck:** Virtuelle [[Prozessor|Prozessoren]] lösen das Problem der Blockierung bei Ein-/Ausgabeoperationen, ermöglichen die Nutzung von Parallelität auf Multicore-Systemen und reduzieren den Overhead durch teure [[Prozess|Prozesswechsel]]. Sie verbessern die Strukturierung komplexer Anwendungen und verstecken Netzwerklatenz in [[Verteiltes System|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Virtuelle [[Prozessor|Prozessoren]] sollten nicht genutzt werden, wenn Speichersicherheit kritisch ist, da [[Thread|Threads]] denselben Adressraum teilen und fehleranfällig sind. Alternativen wie [[Prozess|Prozesse]] bieten bessere Isolation, sind aber teurer im Kontextwechsel. Kernel-basierte [[Thread|Threads]] sind weniger effizient als User-Space-Implementierungen, aber robuster bei blockierenden Operationen.
- **Beispiel / Code:** Ein Multithread-Webclient lädt mehrere Dateien parallel:
```
// Pseudocode für einen Multithread-Webclient
for (Datei in HTML-Seite.benoetigteDateien) {
    Thread.start(() -> {
        Daten = HTTP_Request(Datei.URL);
        Browser.anzeigen(Daten);
    });
}
```

Ein Dateiserver mit Multithreading:
- Singlethread: ~15 Anfragen/Sekunde (5 ms + 1/3 * 60 ms Blockierung).
- Multithread: ~200 Anfragen/Sekunde (Parallelisierung der Blockierungen).
