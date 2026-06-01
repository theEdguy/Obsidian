---
id: ab01dc82-6b65-42c2-800a-30e00267e609
title: "Endlicher Automat (State Machine)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - verteilte-systeme
  - ereignisverarbeitung
  - server-architektur
  - nicht-blockierend
  - zustandsmodellierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Endlicher Automat (State Machine)]]

- **Kernkonzept:** Ein [[Endlicher Automat|Endlicher Automat]] modelliert ein System mit einer begrenzten Anzahl von [[Zustand|Zuständen]] und [[Übergang|Übergängen]], die durch [[Ereignis|Ereignisse]] ausgelöst werden. Er dient zur Steuerung von [[Prozess|Prozessen]] in [[Verteiltes System|Verteilten Systemen]] durch deterministische [[Zustandswechsel]].
- **Nutzen & Zweck:** Der [[Endliche Automat|Endliche Automat]] löst das Problem der [[Komplexitätsreduktion]] in [[Ereignisgesteuerte Systeme|ereignisgesteuerten Systemen]], indem er [[Kontrollfluss|Kontrollflüsse]] strukturiert und [[Parallelität]] ohne [[Thread|Threads]] ermöglicht. Er vermeidet [[Blockierung]] durch nicht-blockierende [[Systemaufruf|Systemaufrufe]] und verbessert die [[Skalierbarkeit]] von [[Server|Servern]].
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit dynamischen [[Zustand|Zuständen]] oder hoher [[Zustandsraum|Zustandsraumkomplexität]], da die Anzahl der [[Zustand|Zustände]] statisch ist. Unterscheidet sich von [[Thread|Threads]] durch fehlende [[Parallelität]] auf [[Prozessor|Prozessorebene]] und von [[Multithreaded Server|Multithreaded Servern]] durch sequentielle [[Ereignisverarbeitung]].
- **Beispiel / Code:** Ein einfacher [[Endlicher Automat|Endlicher Automat]] für einen [[Dateiserver]]:

Zustände: IDLE, READING, WRITING
Ereignisse: read_request, write_request, done

Übergänge:
- IDLE + read_request → READING
- READING + done → IDLE
- IDLE + write_request → WRITING
- WRITING + done → IDLE

Pseudocode:
```
state = IDLE
while true:
    event = wait_for_event()
    if state == IDLE and event == read_request:
        state = READING
        non_blocking_read()
    elif state == READING and event == done:
        state = IDLE
    elif state == IDLE and event == write_request:
        state = WRITING
        non_blocking_write()
    elif state == WRITING and event == done:
        state = IDLE
```
