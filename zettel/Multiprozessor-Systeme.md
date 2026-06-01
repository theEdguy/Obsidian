---
id: 76a4e961-d346-4a62-938b-7e7e7009a89f
title: "Multiprozessor-Systeme"
date: 2026-06-01
tags:
  - verteilte_systeme
  - parallelverarbeitung
  - hardware
  - skalierbarkeit
  - multithreading
  - betriebssysteme
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Multiprozessor-Systeme]]

- **Kernkonzept:** Multiprozessor-Systeme nutzen mehrere physikalische [[Prozessor|Prozessoren]] oder [[Prozessorkern|Prozessorkerne]] innerhalb eines Systems, um [[Thread|Threads]] oder [[Prozess|Prozesse]] parallel auszuführen und so die Leistung durch echte Parallelität zu steigern.
- **Nutzen & Zweck:** Sie lösen das Problem der begrenzten Skalierbarkeit von Single-Prozessor-Systemen, indem sie [[Rechenleistung]] durch parallele Verarbeitung erhöhen. Besonders nützlich für rechenintensive Anwendungen, [[Server|Server-Architekturen]] oder [[Verteilte Systeme|verteilte Systeme]], die hohe [[Durchsatz|Durchsätze]] und [[Lastverteilung|Lastverteilung]] erfordern.
- **Abgrenzung & Grenzen:** Nicht sinnvoll für Anwendungen mit hohem [[Serialisierungsgrad|Serialisierungsgrad]] (z. B. stark abhängige [[Algorithmus|Algorithmen]]), da [[Amdahls Gesetz|Amdahls Gesetz]] die Effizienz begrenzt. Alternativen wie [[Multithreading]] (ohne echte Parallelität) oder [[Verteilte Systeme]] (mit höherer Latenz) können je nach [[Anwendungsfall]] besser geeignet sein. Zudem erfordern Multiprozessor-Systeme komplexere [[Synchronisation]] und [[Speicherverwaltung]].
- **Beispiel / Code:** // Beispiel: Parallelisierung mit OpenMP auf einem Multiprozessor-System
#include <omp.h>
#include <stdio.h>

int main() {
    #pragma omp parallel
    {
        int thread_id = omp_get_thread_num();
        printf("Thread %d führt parallele Arbeit aus.\n", thread_id);
    }
    return 0;
}

// Erläuterung:
// - Das Programm nutzt mehrere Threads, die auf verschiedenen Prozessorkernen laufen.
// - Jeder Thread führt unabhängige Aufgaben aus, was die Gesamtlaufzeit reduziert.
