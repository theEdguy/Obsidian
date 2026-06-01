---
id: 9f7ab285-1ee6-42c7-b51d-759b9292bf16
title: "Prozesse"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - parallelität
  - betriebssysteme
  - kontextwechsel
  - virtualisierung
  - client-server-architektur
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Prozesse]]

- **Kernkonzept:** Ein [[Prozess]] ist ein Software-[[Prozessor]], in dessen Kontext ein oder mehrere [[Thread|Threads]] ablaufen. Er stellt einen isolierten Ausführungskontext mit eigenem Adressraum dar, während [[Thread|Threads]] innerhalb eines [[Prozess|Prozesses]] Ressourcen teilen und als minimale Ausführungseinheiten fungieren.
- **Nutzen & Zweck:** Prozesse ermöglichen die parallele Ausführung von [[Programm|Programmen]] in [[Verteiltes System|verteilten Systemen]] und bieten Isolation für Stabilität und Sicherheit. [[Thread|Threads]] lösen das Problem der Blockierung bei E/A-Operationen, nutzen Parallelität auf Multicore-Systemen und vermeiden teure [[Prozess|Prozesswechsel]]. Sie verbessern die Effizienz und Strukturierung von Anwendungen, insbesondere in Client-Server-Architekturen.
- **Abgrenzung & Grenzen:** Prozesse sind ressourcenintensiv (Speicher, Kontextwechsel) und sollten nicht für feingranulare Parallelität genutzt werden – hier sind [[Thread|Threads]] effizienter. [[Thread|Threads]] sind jedoch fehleranfälliger, da sie sich denselben Adressraum teilen und keine hardwaregestützte Isolation bieten. In sicherheitskritischen Szenarien sind [[Prozess|Prozesse]] vorzuziehen. Alternativen wie nichtblockierende Systemaufrufe oder endliche Automaten können in speziellen Fällen sinnvoll sein.
- **Beispiel / Code:** ```c
// Beispiel: Multithreaded Server (Dispatcher/Worker-Modell)
#include <pthread.h>
#include <stdio.h>

void* worker_thread(void* arg) {
    int request = *(int*)arg;
    printf("Verarbeite Request %d\n", request);
    // Blockierender E/A-Aufruf (z. B. Dateizugriff)
    return NULL;
}

int main() {
    pthread_t threads[5];
    int requests[5] = {1, 2, 3, 4, 5};
    
    // Starte Worker-Threads
    for (int i = 0; i < 5; i++) {
        pthread_create(&threads[i], NULL, worker_thread, &requests[i]);
    }
    
    // Warte auf Abschluss
    for (int i = 0; i < 5; i++) {
        pthread_join(threads[i], NULL);
    }
    return 0;
}
```

**Erläuterung**: Der Dispatcher (Hauptthread) verteilt Requests an Worker-Threads. Während ein Thread blockiert (z. B. bei Festplattenzugriff), können andere weiterarbeiten. Dies versteckt Netzwerklatenz und nutzt Parallelität.
