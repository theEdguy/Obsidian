---
id: 0b22f2d7-a10d-4704-a027-08d2c7965248
title: "Blockierende und nicht-blockierende Systemaufrufe"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - systemaufrufe
  - ein-ausgabe
  - parallelisierung
  - skalierbarkeit
  - e-a-operationen
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Blockierende und nicht-blockierende Systemaufrufe]]

- **Kernkonzept:** Ein [[Systemaufruf|Systemaufruf]] kann entweder [[blockierend|blockierend]] oder [[nicht-blockierend|nicht-blockierend]] sein. [[Blockierende Systemaufrufe|Blockierende Systemaufrufe]] unterbrechen die Ausführung eines [[Thread|Threads]] oder [[Prozess|Prozesses]], bis eine Bedingung (z. B. Abschluss einer [[E/A-Operation|E/A-Operation]]) erfüllt ist, während [[nicht-blockierende Systemaufrufe]] es ermöglichen, während des [[Aufruf|Aufrufs]] weiterzuarbeiten, oft durch [[asynchrone Programmierung|asynchrone]] oder [[ereignisgesteuerte Programmierung|ereignisgesteuerte]] Mechanismen.
- **Nutzen & Zweck:** [[Blockierende Systemaufrufe]] vereinfachen die [[Programmstruktur]] durch automatisches Pausieren von [[Thread|Threads]] oder [[Prozess|Prozessen]] während des Wartens auf Ressourcen, was die [[Ressourcennutzung]] in [[Einzelprozessor-System|Einzelprozessor-Systemen]] optimiert. [[Nicht-blockierende Systemaufrufe]] hingegen verbessern die [[Effizienz]] und [[Skalierbarkeit]] von [[System|Systemen]], insbesondere in [[verteilten Systemen]], indem sie [[Latenz|Latenzzeiten]] verstecken und [[Parallelität]] ermöglichen. Sie lösen das Problem der [[Blockierung]] in [[Single-Thread|Single-Threaded]]-Umgebungen, wo [[E/A-Operation|E/A-Operationen]] sonst den gesamten [[Prozess]] lahmlegen würden.
- **Abgrenzung & Grenzen:** [[Blockierende Systemaufrufe]] sind ungeeignet für [[Anwendung|Anwendungen]] mit kritischen [[Latenz|Latenzanforderungen]] oder hohem [[Parallelitätsbedarf]], da sie zu [[Performance-Engpässen]] führen können. [[Nicht-blockierende Systemaufrufe]] erfordern komplexere [[Implementierung|Implementierungen]], oft mit [[Ereignis|Ereignis]]-Schleifen oder [[Callback|Callbacks]], und sind weniger intuitiv für sequentielle [[Verarbeitungslogik|Verarbeitungslogiken]]. Alternativen wie [[Multithreading]] oder [[Endlicher Automat|endliche Automaten]] können je nach [[Anforderung|Anforderungen]] besser geeignet sein. In [[verteilten Systemen]] müssen beide Ansätze sorgfältig abgewogen werden, um [[Deadlock|Deadlocks]] oder [[Race_Condition|Race Conditions]] zu vermeiden.
- **Beispiel / Code:** ### Blockierender Systemaufruf (C):
```c
#include <unistd.h>
#include <stdio.h>

int main() {
    char buffer[256];
    // Blockierender Leseaufruf: Prozess wartet, bis Daten verfügbar sind
    ssize_t bytes_read = read(STDIN_FILENO, buffer, sizeof(buffer));
    printf("Gelesen: %zd Bytes\n", bytes_read);
    return 0;
}
```

### Nicht-blockierender Systemaufruf (Python):
```python
import socket

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.setblocking(False)
try:
    sock.connect(('example.com', 80))
except BlockingIOError:
    # Verbindung wird asynchron aufgebaut
    print("Verbindung wird im Hintergrund aufgebaut...")
```

In [[verteilten Systemen]] werden nicht-blockierende [[E/A-Operation|E/A-Operationen]] oft mit [[Ereignis|Ereignis]]-Bibliotheken wie `select` oder `epoll` kombiniert, um mehrere [[Aufruf|Aufrufe]] gleichzeitig zu verwalten. Ein [[Multithreaded-Server]] kann blockierende [[Aufruf|Aufrufe]] in separaten [[Thread|Threads]] ausführen, während nicht-blockierende Ansätze [[Ereignis|Ereignis]]-Schleifen nutzen, um [[Skalierbarkeit]] zu erhöhen.
