---
id: 91612f53-d435-44f9-b89a-87ec3566f445
title: "Adressraum"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - speicherverwaltung
  - virtualisierung
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Adressraum]]

- **Kernkonzept:** Der Adressraum bezeichnet den virtuellen Speicherbereich, auf den ein [[Prozess]] oder [[Thread]] zugreifen kann. Er ermöglicht die Isolation und Verwaltung von [[Speicher|Speicherbereichen]] für verschiedene [[Prozess|Prozesse]] oder [[Thread|Threads]] innerhalb eines Systems.
- **Nutzen & Zweck:** Der Adressraum löst das Problem der Speicherkollisionen und [[Sicherheit|Sicherheitsrisiken]] in [[Multitasking|multitaskingfähigen]] Systemen, indem er jedem [[Prozess]] einen eigenen, geschützten Bereich zuweist. Er ermöglicht effiziente [[Speicherverwaltung]] und vereinfacht die [[Parallelisierung]] von [[Thread|Threads]] innerhalb eines [[Prozess|Prozesses]].
- **Abgrenzung & Grenzen:** Ein gemeinsamer Adressraum sollte nicht genutzt werden, wenn strikte Isolation zwischen [[Prozess|Prozessen]] erforderlich ist (z. B. bei [[Sicherheitskritische Anwendung|sicherheitskritischen Anwendungen]]), da [[Thread|Threads]] desselben [[Prozess|Prozesses]] sich gegenseitig beeinflussen können. Alternativen wie separate [[Prozess|Prozesse]] mit eigenem Adressraum sind hier vorzuziehen, auch wenn sie teurere [[Kontextwechsel]] erfordern.
- **Beispiel / Code:** In einem Multi-Threaded-Programm teilen sich alle [[Thread|Threads]] denselben Adressraum. Beispiel in C mit POSIX-Threads:

```c
#include <pthread.h>
#include <stdio.h>

int shared_data = 0; // Gemeinsamer Adressraum

void* thread_function(void* arg) {
    shared_data++; // Zugriff auf gemeinsamen Speicher
    printf("Thread %ld: shared_data = %d\n", (long)arg, shared_data);
    return NULL;
}

int main() {
    pthread_t thread1, thread2;
    pthread_create(&thread1, NULL, thread_function, (void*)1);
    pthread_create(&thread2, NULL, thread_function, (void*)2);
    pthread_join(thread1, NULL);
    pthread_join(thread2, NULL);
    return 0;
}
```

Hier greifen beide [[Thread|Threads]] auf die Variable `shared_data` zu, die im gemeinsamen Adressraum liegt.
