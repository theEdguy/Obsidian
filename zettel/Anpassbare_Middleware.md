---
id: 02b82159-a203-42a9-af96-3728c45906c5
title: "Anpassbare Middleware"
date: 2026-06-01
tags:
  - verteilte_systeme
  - middleware
  - verteilte-systeme
  - architektur
  - interzeptoren
  - anpassbarkeit
  - software-engineering
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Anpassbare Middleware]]

- **Kernkonzept:** Anpassbare [[Middleware]] ermöglicht die gezielte Modifikation des Verhaltens einer [[Middleware|Middleware-Komponente]], um spezifische Anforderungen von [[Anwendung|Anwendungen]] zu erfüllen, ohne deren grundlegende [[Funktionalität]] zu verändern. Dies erfolgt oft durch [[Interzeptor|Interzeptoren]], die den [[Kontrollfluss]] unterbrechen und anpassen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]], dass [[Middleware]] meist generische [[Funktionalität|Funktionalitäten]] für eine breite [[Anwendung|Anwendungsmasse]] bereitstellt, aber individuelle [[Anpassung|Anpassungen]] für spezifische [[Anwendung|Anwendungsfälle]] fehlen. Es ermöglicht [[Erweiterung|Erweiterungen]] oder [[Modifikation|Modifikationen]] ohne die [[Middleware]] neu zu implementieren.
- **Abgrenzung & Grenzen:** Anpassbare [[Middleware]] sollte nicht genutzt werden, wenn die [[Anwendung]] keine spezifischen [[Anpassung|Anpassungen]] benötigt oder wenn die [[Komplexität]] der [[Interzeptor|Interzeptoren]] die [[Wartbarkeit]] beeinträchtigt. Alternativen wie [[Wrapper]] oder [[Broker]] sind besser geeignet, wenn nur [[Interface|Interfaces]] transformiert werden müssen, ohne den [[Kontrollfluss]] zu unterbrechen.
- **Beispiel / Code:** Ein Beispiel für einen Request-Level-Interzeptor in einer [[Middleware]]:

```
// Client-Anwendung ruft B.doit(val) auf
// Request-Level-Interzeptor fängt den Aufruf ab und modifiziert ihn
invoke(B, &doit, val) {
    log("Aufruf von doit mit Wert: " + val);  // Zusätzliche Logik
    val = transform(val);  // Anpassung des Parameters
    return original_invoke(B, &doit, val);  // Weiterleitung an die Middleware
}
```

Hier wird der [[Kontrollfluss]] unterbrochen, um Logging oder Parametertransformationen durchzuführen.
