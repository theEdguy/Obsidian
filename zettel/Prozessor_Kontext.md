---
id: d4d00cff-83f2-4f54-b138-c1df9e21f93c
title: "Prozessor Kontext"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - hardware
  - betriebssysteme
  - kontextwechsel
  - register
  - multitasking
  - threads
  - kontextverwaltung
  - parallelität
  - ressourcenmanagement
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Prozessor Kontext]]

- **Kernkonzept:** Der [[Prozessor_Kontext|Prozessor Kontext]] bezeichnet die minimale Sammlung von [[Registerwert|Registerwerten]] (z. B. [[Stack_Pointer|Stack Pointer]], [[Programmzähler|Programmzähler]]), die zur Ausführung einer [[Instruktion|Instruktionsgruppe]] auf einem [[Prozessor]] erforderlich ist. Er ist ein Teil des umfassenderen [[Prozess_Kontext|Prozesskontexts]], der zusätzlich [[Speicheradresse|Speicherwerte]], [[MMU]]-Register und [[Thread_Kontext|Thread-spezifische Daten]] umfasst, um die Ausführung von [[Thread|Threads]] innerhalb eines [[Prozess|Prozesses]] zu ermöglichen.
- **Nutzen & Zweck:** Der [[Prozessor_Kontext|Prozessor Kontext]] löst das Problem der [[Unterbrechung|Unterbrechbarkeit]] und [[Wiederaufnahme|Wiederaufnahme]] von [[Prozess|Prozessen]] oder [[Thread|Threads]] auf Hardware-Ebene, indem er den Zustand eines [[Prozessors]] sichert. Ohne ihn wäre [[Multitasking]] in [[Betriebssystem|Betriebssystemen]] unmöglich, da der Zustand nicht gesichert und wiederhergestellt werden könnte. Der erweiterte [[Prozess_Kontext|Prozesskontext]] ermöglicht darüber hinaus eine effiziente [[Ressourcenverwaltung]] und [[Parallelität]], indem er zusätzliche Systemressourcen wie [[MMU]]-Register und [[Adressraum|Adressräume]] berücksichtigt.
- **Abgrenzung & Grenzen:** Der [[Prozessor_Kontext|Prozessor Kontext]] ist spezifisch für die Hardware-Ebene und umfasst keine [[Speicheradresse|Speicherwerte]] oder [[Zustand|Zustände]] höherer Abstraktionsebenen wie [[Thread_Kontext|Threadkontext]] oder [[Prozess_Kontext|Prozesskontext]]. Während der [[Prozessor_Kontext]] nur die minimalen Hardware-Register betrifft, erfordert ein [[Kontextwechsel]] auf [[Thread]]- oder [[Prozess]]-Ebene zusätzliche Daten wie [[MMU]]-Register oder [[Adressraum|Adressraum]]-Informationen. Der [[Prozess_Kontext|Prozesskontext]] ist aufwendiger zu sichern als ein [[Thread_Kontext|Threadkontext]] und sollte vermieden werden, wenn [[Leichtgewichtigkeit]] oder schnelle [[Kontextwechsel]] Priorität haben – hier sind [[Thread|Threads]] vorzuziehen, da sie denselben [[Adressraum]] teilen und Speicherzugriffskonflikte begünstigen können.
- **Beispiel / Code:** Ein einfaches Beispiel für die Sicherung eines [[Prozessor_Kontext|Prozessor Kontexts]] in Assembler (x86-Architektur) sowie ein Pseudocode-Beispiel für einen [[Prozess_Kontext|Prozesskontext]]-Wechsel:

**Prozessor Kontext (Assembler x86):**
```asm
; Sicherung des aktuellen Kontexts
PUSH EAX      ; Allgemeines Register
PUSH EBX      ; Allgemeines Register
PUSH ECX      ; Allgemeines Register
PUSH EDX      ; Allgemeines Register
PUSH ESP      ; Stack Pointer
PUSH EBP      ; Base Pointer
PUSH EIP      ; Programmzähler (wird oft implizit durch CALL/RET gesichert)
PUSH EFLAGS   ; Statusregister

; ... Unterbrechung oder Wechsel ...

; Wiederherstellung des Kontexts
POP EFLAGS    ; Statusregister
POP EIP       ; Programmzähler
POP EBP       ; Base Pointer
POP ESP       ; Stack Pointer
POP EDX       ; Allgemeines Register
POP ECX       ; Allgemeines Register
POP EBX       ; Allgemeines Register
POP EAX       ; Allgemeines Register
```

**Prozess Kontext (Pseudocode):**
```
void context_switch(Process* old, Process* new) {
    save_context(old->context);  // Sichern des aktuellen Prozesskontexts
    // Enthält: Programmzähler, Stack Pointer, MMU-Register, Thread-Zustand
    load_context(new->context);   // Laden des neuen Prozesskontexts
}
```
