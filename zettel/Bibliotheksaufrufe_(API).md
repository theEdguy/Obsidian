---
id: 879df6c4-8731-4824-8e9b-2935cbc455d6
title: "Bibliotheksaufrufe (API)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - abstraktion
  - schnittstelle
  - softwareentwicklung
  - modularität
  - virtualisierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Bibliotheksaufrufe (API)]]

- **Kernkonzept:** Bibliotheksaufrufe [[Bibliotheksaufruf|Bibliotheksaufrufe]] (API) stellen eine standardisierte Schnittstelle bereit, über die [[Anwendung|Anwendungen]] mit Systemfunktionen oder [[Dienst|Diensten]] interagieren, ohne deren interne [[Implementierung]] zu kennen.
- **Nutzen & Zweck:** Sie ermöglichen die [[Abstraktion]] von Komplexität, fördern die [[Wiederverwendbarkeit]] von [[Code]] und erleichtern die [[Portierbarkeit]] von [[Software]] über verschiedene [[Plattform|Plattformen]]. Zudem trennen sie die [[Schnittstelle]] von der [[Implementierung]], was die [[Modularität]] und [[Wartbarkeit]] verbessert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Low-Level-Operation|Low-Level-Operationen]], die direkte [[Hardware]]-Zugriffe erfordern. Im Vergleich zu [[Systemaufruf|Systemaufrufen]] sind Bibliotheksaufrufe [[Benutzermodus|benutzermodus]]-basiert und bieten keine [[Privilegien|privilegierten]] Operationen. Bei [[Performance]]-kritischen Anwendungen können sie durch direkte [[Systemaufruf|Systemaufrufe]] ersetzt werden.
- **Beispiel / Code:** Ein Beispiel in C für einen Bibliotheksaufruf der Standard-C-Bibliothek:

```c
#include <stdio.h>

int main() {
    FILE *file = fopen("beispiel.txt", "r"); // Bibliotheksaufruf (API)
    if (file != NULL) {
        printf("Datei erfolgreich geöffnet.\n");
        fclose(file);
    }
    return 0;
}
```

Hier wird die `fopen`-Funktion der C-Standardbibliothek genutzt, um eine Datei zu öffnen, ohne die zugrundeliegenden [[Systemaufruf|Systemaufrufe]] zu kennen.
