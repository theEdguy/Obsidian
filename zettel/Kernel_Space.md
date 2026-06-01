---
id: e69de410-efa1-470f-adad-fae75112b7ed
title: "Kernel Space"
date: 2026-06-01
tags:
  - verteilte_systeme
  - betriebssysteme
  - virtualisierung
  - prozesse
  - sicherheit
  - hardware-abstraktion
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Kernel Space]]

- **Kernkonzept:** Der Kernel Space bezeichnet den geschützten [[Adressraum|Adressräumen]] des [[Betriebssystem|Betriebssystems]], in dem kritische [[Operation|Operationen]] wie [[Hardware]]-Zugriff oder [[Prozess]]-Verwaltung ausgeführt werden. Er trennt privilegierte [[Funktion|Funktionen]] von [[Anwendung|Anwendungen]] im User Space.
- **Nutzen & Zweck:** Der Kernel Space löst das Problem der [[Sicherheit]] und [[Stabilität]] in [[System|Systemen]], indem er [[Ressource|Ressourcen]] vor unbefugtem Zugriff schützt und [[Systemaufruf|Systemaufrufe]] als kontrollierte Schnittstelle bereitstellt. Er ermöglicht [[Multitasking]] und [[Hardware]]-Abstraktion.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn [[Echtzeit]]-Anforderungen oder minimale [[Latenz]] kritisch sind, da [[Kontextwechsel]] zwischen User Space und Kernel Space [[Overhead]] verursachen. Alternativen wie [[Userspace-Treiber]] oder [[unikernel]]-Architekturen vermeiden diesen [[Moduswechsel]], bieten aber weniger [[Isolation]].
- **Beispiel / Code:** Ein [[Systemaufruf]] wie `open()` in C wechselt vom User Space in den Kernel Space:
```c
#include <fcntl.h>
int fd = open("/path/to/file", O_RDONLY); // Wechsel zu Kernel Space
```
Der Kernel prüft Berechtigungen und führt die [[Dateioperation]] aus, bevor die Kontrolle an den User Space zurückgegeben wird.
