---
id: e592847c-0f08-45bd-a6ed-a3caf9872151
title: "Multicore-Prozessoren"
date: 2026-06-01
tags:
  - verteilte_systeme
  - hardware
  - parallelverarbeitung
  - multithreading
  - prozessorarchitektur
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Multicore-Prozessoren]]

- **Kernkonzept:** Multicore-Prozessoren integrieren mehrere [[Prozessorkern|Prozessorkerne]] auf einem einzigen Chip, um parallele Ausführung von [[Thread|Threads]] oder [[Prozess|Prozessen]] zu ermöglichen und die Leistung durch echte Hardware-Parallelität zu steigern.
- **Nutzen & Zweck:** Sie lösen das Problem der physikalischen Grenzen der [[Taktrate|Taktraten]]-Skalierung (Power Wall, Heat Wall) und ermöglichen effizientere Nutzung von [[Mehrkernarchitektur|Mehrkernarchitekturen]] für [[Parallelverarbeitung|parallele Verarbeitung]], insbesondere in [[Verteiltes System|verteilten Systemen]] und [[Multithread-Programmierung|multithreaded]] Anwendungen.
- **Abgrenzung & Grenzen:** Nicht sinnvoll bei rein sequentiellen [[Algorithmus|Algorithmen]], die keine Parallelisierung erlauben. Im Vergleich zu [[Singlecore-Prozessor|Singlecore-Prozessoren]] erfordern sie komplexere [[Synchronisation|Synchronisationsmechanismen]] (z. B. [[Lock|Locks]], [[Race Condition|Race Conditions]]). Alternativen wie [[Hyper-Threading]] oder [[GPU-Computing]] können in spezifischen Szenarien effizienter sein.
- **Beispiel / Code:** Ein einfaches Beispiel in C mit POSIX-Threads (pthreads) zur Nutzung von Multicore-Prozessoren:

```c
#include <pthread.h>
#include <stdio.h>

void* thread_function(void* arg) {
    int thread_id = *(int*)arg;
    printf("Thread %d läuft auf Kern %d\n", thread_id, sched_getcpu());
    return NULL;
}

int main() {
    pthread_t threads[4];
    int thread_ids[4] = {0, 1, 2, 3};
    
    for (int i = 0; i < 4; i++) {
        pthread_create(&threads[i], NULL, thread_function, &thread_ids[i]);
    }
    
    for (int i = 0; i < 4; i++) {
        pthread_join(threads[i], NULL);
    }
    
    return 0;
}
```

*Erläuterung*: Das Programm startet vier [[Thread|Threads]], die parallel auf verschiedenen [[Prozessorkern|Kernen]] eines Multicore-Prozessors ausgeführt werden können. Die Funktion `sched_getcpu()` zeigt, auf welchem Kern der Thread läuft.
