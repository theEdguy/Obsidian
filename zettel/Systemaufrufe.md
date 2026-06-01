---
id: 91a24daa-ed96-4593-9bb4-3eda83574fc5
title: "Systemaufrufe"
date: 2026-06-01
tags:
  - verteilte_systeme
  - betriebssysteme
  - prozesse
  - virtualisierung
  - schnittstellen
  - ressourcenverwaltung
  - kernel
  - systemprogrammierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Systemaufrufe]]

- **Kernkonzept:** Systemaufrufe sind Schnittstellen zwischen [[Anwendungsprogramm|Anwendungsprogrammen]] und dem [[Betriebssystem]], die es [[Prozess|Prozessen]] ermöglichen, privilegierte [[Operation|Operationen]] wie [[Dateizugriff|Dateizugriffe]] oder [[Netzwerkkommunikation]] sicher auszuführen. Sie erzwingen einen Wechsel vom [[Usermodus]] in den [[Kernelmodus]], um [[Hardware|Hardware-Ressourcen]] kontrolliert zu nutzen.
- **Nutzen & Zweck:** Systemaufrufe lösen das Problem der sicheren und kontrollierten [[Ressourcenverwaltung]] in [[Multitasking-Systemen]]. Sie ermöglichen [[Isolation]] zwischen [[Prozess|Prozessen]], schützen das [[Betriebssystem]] vor fehlerhaften [[Anwendungsprogramm|Anwendungen]] und bieten eine standardisierte [[Schnittstelle]] für [[Hardware]]-Zugriffe, ohne dass [[Anwendungsentwickler|Entwickler]] direkte [[Hardware]]-Kenntnisse benötigen.
- **Abgrenzung & Grenzen:** Systemaufrufe sollten nicht für [[Operation|Operationen]] genutzt werden, die keine privilegierten [[Ressource|Ressourcen]] benötigen, da sie durch den [[Moduswechsel]] (Usermodus ↔ Kernelmodus) [[Performance|Performance-Overhead]] verursachen. Alternativen sind [[Bibliotheksfunktion|Bibliotheksfunktionen]] (z. B. mathematische Berechnungen) oder [[Userspace-Threading]], das ohne [[Betriebssystem]]-Intervention auskommt. Im Vergleich zu [[Hypercall|Hypercalls]] (für [[Virtualisierung]]) sind Systemaufrufe auf [[Betriebssystem]]-Ebene beschränkt.
- **Beispiel / Code:** Ein einfacher Systemaufruf in C zum Öffnen einer Datei:
```c
#include <fcntl.h>
#include <unistd.h>

int main() {
    int fd = open("datei.txt", O_RDONLY); // Systemaufruf: Wechsel in Kernelmodus
    if (fd == -1) {
        perror("Fehler beim Öffnen");
        return 1;
    }
    close(fd); // Systemaufruf: Ressource freigeben
    return 0;
}
```
Der Aufruf `open()` erfordert einen Wechsel in den Kernelmodus, um Datei-Deskriptoren zu verwalten und [[Zugriffsrecht|Zugriffsrechte]] zu prüfen.
