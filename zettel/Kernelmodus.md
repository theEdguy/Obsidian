---
id: 6b11c252-add6-4ba8-b7ad-3882523d6a17
title: "Kernelmodus"
date: 2026-06-01
tags:
  - verteilte_systeme
  - betriebssysteme
  - prozesse
  - hardware
  - sicherheit
  - virtualisierung
  - kontextwechsel
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Kernelmodus]]

- **Kernkonzept:** Der Kernelmodus ist ein privilegierter [[Betriebsmodus|Betriebsmodi]] eines Prozessors, in dem das [[Betriebssystem]] kritische [[Operation|Operationen]] ausführt, die direkten Zugriff auf [[Hardware]]-Ressourcen oder geschützte [[Speicherbereich|Speicherbereiche]] erfordern. Im Gegensatz zum Usermodus sind hier alle [[Befehlssatzarchitektur|Maschineninstruktionen]] erlaubt.
- **Nutzen & Zweck:** Der Kernelmodus löst das Problem der [[Sicherheit]] und [[Stabilität]] in [[System|Systemen]], indem er verhindert, dass [[Anwendungsprogramm|Anwendungsprogramme]] direkt auf kritische [[Hardware]]-Ressourcen zugreifen oder das [[Betriebssystem]] beschädigen. Er ermöglicht die [[Isolation]] von [[Prozess|Prozessen]] und die effiziente Verwaltung von [[Systemressource|Systemressourcen]].
- **Abgrenzung & Grenzen:** Der Kernelmodus sollte nicht für [[Anwendungslogik]] genutzt werden, da er [[Performance]]-Einbußen durch häufige [[Kontextwechsel]] verursacht und das [[System]] anfälliger für [[Fehler]] oder [[Sicherheitslücke|Sicherheitslücken]] macht. Alternativen wie [[Userspace-Thread|Userspace-Threads]] oder [[Virtualisierung]] können für weniger kritische [[Operation|Operationen]] effizienter sein.
- **Beispiel / Code:** Ein typisches Beispiel ist der Wechsel vom Usermodus in den Kernelmodus bei einem [[Systemaufruf]] wie `read()`:

```c
#include <unistd.h>

int main() {
    char buffer[100];
    // Wechsel in den Kernelmodus, um Daten von der Festplatte zu lesen
    read(STDIN_FILENO, buffer, sizeof(buffer));
    return 0;
}
```

Hier löst der `read()`-Aufruf einen [[Kontextwechsel]] in den Kernelmodus aus, um die [[E/A-Operation]] durchzuführen.
