---
id: 26ced737-c092-4a12-809b-655a3f25d9a9
title: "Kontextwechsel"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - betriebssysteme
  - parallelität
  - verteilte-systeme
  - kontextverwaltung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Kontextwechsel]]

- **Kernkonzept:** Ein [[Kontextwechsel]] bezeichnet das Speichern und Wiederherstellen des Zustands eines [[Thread|Threads]] oder [[Prozess|Prozesses]], um die Ausführung eines anderen [[Thread|Threads]] oder [[Prozess|Prozesses]] auf einem [[Prozessor]] zu ermöglichen. Dies umfasst das Sichern von Registerwerten, [[Speicher]]adressen und [[Zustand|Zuständen]] wie Programmzähler oder Stack-Pointer.
- **Nutzen & Zweck:** Der [[Kontextwechsel]] ermöglicht [[Multitasking]] und effiziente Nutzung von [[Prozessor]]ressourcen, indem [[Thread|Threads]] oder [[Prozess|Prozesse]] scheinbar parallel ausgeführt werden. Er löst das Problem der [[Blockierung]] bei [[E/A-Operation|E/A-Operationen]] und verbessert die [[Parallelität]] in [[Multicore-System|Multicore-Systemen]].
- **Abgrenzung & Grenzen:** Ein [[Kontextwechsel]] ist teurer bei [[Prozess|Prozessen]] als bei [[Thread|Threads]], da das [[Betriebssystem]] involviert ist (Wechsel in den [[Kernelmodus]]). Bei [[Thread|Threads]] im selben [[Adressraum]] ist er effizienter, aber fehleranfälliger, da keine hardwaregestützte [[Isolation]] besteht. Alternativen wie [[nichtblockierende Systemaufrufe]] oder [[Endliche Automaten]] vermeiden [[Kontextwechsel]], sind aber komplexer zu implementieren.
- **Beispiel / Code:** Ein einfaches Beispiel für einen [[Thread-Kontextwechsel]] in C mit POSIX-Threads:

```c
#include <pthread.h>
#include <stdio.h>

void* thread_function(void* arg) {
    printf("Thread läuft mit ID: %lu\n", pthread_self());
    return NULL;
}

int main() {
    pthread_t thread1, thread2;
    pthread_create(&thread1, NULL, thread_function, NULL);
    pthread_create(&thread2, NULL, thread_function, NULL);
    
    // Der Scheduler führt einen Kontextwechsel zwischen thread1 und thread2 durch
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);
    return 0;
}
```

Hier wechselt das [[Betriebssystem]] zwischen den [[Thread|Threads]], sobald ein [[Thread]] blockiert oder seine [[Zeitscheibe]] abgelaufen ist.
