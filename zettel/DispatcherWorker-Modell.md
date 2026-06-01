---
id: 5510534b-0b35-4823-86d0-d84ec33436a1
title: "Dispatcher/Worker-Modell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architekturmuster
  - verteilte-systeme
  - multithreading
  - lastverteilung
  - parallelverarbeitung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Dispatcher/Worker-Modell]]

- **Kernkonzept:** Das Dispatcher/Worker-Modell ist ein [[Architekturmuster|Architekturmuster]] für [[verteilte Systeme|verteilte Systeme]], bei dem ein [[Dispatcher|Dispatcher]] eingehende [[Anfrage|Anfragen]] verteilt und [[Worker|Worker]] diese parallel bearbeiten, um [[Skalierbarkeit|Skalierbarkeit]] und [[Effizienz]] zu erhöhen.
- **Nutzen & Zweck:** Es löst das [[Problem]] der [[Lastverteilung]] in [[Server|Servern]] und ermöglicht [[Parallelverarbeitung]] durch [[Multithreading]]. Dadurch werden [[Blockierung|Blockierungen]] vermieden, [[Netzwerklatenz]] versteckt und die [[Auslastung]] von [[Multicore-Prozessoren]] optimiert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]] mit starker [[Abhängigkeit|Abhängigkeiten]] zwischen [[Aufgabe|Aufgaben]] oder hohem [[Synchronisationsbedarf]]. Alternativen sind [[Single-Threaded-Server]] (einfacher, aber keine Parallelität) oder [[Endliche Automaten]] (nicht-blockierend, aber komplexer).
- **Beispiel / Code:** ```python
# Pseudocode für Dispatcher/Worker-Modell
import threading
import queue

# Worker-Funktion
def worker(task_queue):
    while True:
        task = task_queue.get()
        process_task(task)  # Blockierende Operation
        task_queue.task_done()

# Dispatcher
class Dispatcher:
    def __init__(self, num_workers=4):
        self.task_queue = queue.Queue()
        self.workers = [threading.Thread(target=worker, args=(self.task_queue,)) for _ in range(num_workers)]
        for w in self.workers:
            w.start()
    
    def add_task(self, task):
        self.task_queue.put(task)
```
