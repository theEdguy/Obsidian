---
id: 45fcc39a-52de-41ab-9be7-da3bcd02f3f8
title: "E/A-Operationen (Ein-/Ausgabe-Operationen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - verteilte-systeme
  - betriebssysteme
  - parallelisierung
  - e-a-verwaltung
  - kontextwechsel
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[E/A-Operationen (Ein-/Ausgabe-Operationen)]]

- **Kernkonzept:** E/A-Operationen [[E/A-Operation|E/A-Operationen]] ermöglichen die Kommunikation eines [[Prozess|Prozesses]] oder [[Thread|Threads]] mit externen Ressourcen wie Festplatten, Netzwerken oder Peripheriegeräten, wobei der [[Prozess|Prozess]] während blockierender Aufrufe pausiert.
- **Nutzen & Zweck:** Sie lösen das Problem der effizienten Ressourcennutzung, indem sie [[Prozess|Prozesse]] oder [[Thread|Threads]] während Wartezeiten auf externe Datenfreigaben blockieren und so die [[CPU]] für andere Aufgaben freigeben. In [[Verteilte Systeme|verteilten Systemen]] verbergen sie Netzwerklatenzen durch parallele Abwicklung mehrerer Operationen.
- **Abgrenzung & Grenzen:** Blockierende E/A-Operationen sollten vermieden werden, wenn [[Echtzeitanforderung|Echtzeitanforderungen]] bestehen oder wenn die [[Latenz]] kritisch ist. Alternativen wie nicht-blockierende E/A oder [[Event-driven Programming|ereignisgesteuerte Programmierung]] sind hier vorzuziehen. In [[Single-Thread|Single-Thread]]-Umgebungen führen blockierende Aufrufe zur vollständigen Blockade des [[Prozess|Prozesses]].
- **Beispiel / Code:** Ein einfaches Beispiel in Python mit blockierender E/A:
```python
import threading

def read_file(filename):
    with open(filename, 'r') as file:
        data = file.read()  # Blockierender E/A-Aufruf
    print(f"Gelesene Daten: {data}")

# Thread zur parallelen Ausführung
thread = threading.Thread(target=read_file, args=("beispiel.txt",))
thread.start()
```
In [[Verteilte Systeme|verteilten Systemen]] könnte ein [[Multithreaded Server|Multithread-Server]] mehrere Client-Anfragen parallel bearbeiten, während ein Thread auf Netzwerk-E/A wartet.
