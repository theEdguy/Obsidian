---
id: 960ac7c3-62a6-4803-a3d0-7a614560b57a
title: "Vorbedingung"
date: 2026-05-30
tags:
  - software_engineering
  - formale_methode
  - system_design
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Vorbedingung]]

- **Kernkonzept:** Eine [[Vorbedingung]] definiert die Menge der [[Zustand|Zustände]], in denen ein Aufruf einer [[Operation]] zulässig ist. Sie stellt sicher, dass das [[System|System]] sich in einem gültigen Zustand befindet, bevor die [[Operation]] ausgeführt wird.
- **Nutzen & Zweck:** Sie verhindert unerwartetes Verhalten oder [[Fehler|Fehler]] durch unsachgemäße Nutzung von [[Operation|Operationen]] und macht die Anforderungen an den [[Systemzustand]] explizit. Dies fördert die [[Robustheit]] und [[Korrektheit]] des [[System|Systems]].
- **Abgrenzung & Grenzen:** Im Gegensatz zu [[Nachbedingung|Nachbedingungen]] beschreibt eine [[Vorbedingung]] nicht das Ergebnis einer [[Operation]], sondern die Voraussetzungen für deren Ausführung. Sie sollte nicht mit technischen Implementierungsdetails verwechselt werden.
- **Beispiel / Code:** ```java
/**
 * Vorbedingung: Das System muss initialisiert sein.
 * @throws SystemNotInitializedException falls das System nicht initialisiert ist
 */
public void manageMembers(Token token) {
    if (!system.isInitialized()) {
        throw new SystemNotInitializedException();
    }
    // Weitere Logik...
}
```
