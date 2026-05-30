---
id: 42ce2866-dff9-4868-8089-1c5f5acd7e5a
title: "Asynchrone_Anbindung"
date: 2026-05-30
tags:
  - software_engineering
  - architekturmuster
  - konkurrenz
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[Asynchrone_Anbindung]]

- **Kernkonzept:** Ein [[Architekturmuster]], bei dem die [[Benutzeroberfläche]] und die [[Logik]] eines [[Systems]] nicht blockierend miteinander kommunizieren. Die [[Benutzeroberfläche]] bleibt reaktionsfähig, auch wenn die [[Logik]] beschäftigt ist.
- **Nutzen & Zweck:** Verhindert [[Blockierung]] der [[Benutzeroberfläche]] während langer [[Operation|Operationen]] (z. B. [[Netzwerk]]-Anfragen) und verbessert die [[Benutzererfahrung]]. Ermöglicht die [[Parallelisierung]] von [[Aufgabe|Aufgaben]].
- **Abgrenzung & Grenzen:** Nicht notwendig für einfache [[Systeme]] mit kurzen [[Operation|Operationen]]. Unterscheidet sich von [[Synchrone_Kommunikation|synchroner Kommunikation]] durch die nicht-blockierende Natur. Erfordert oft [[Event-gesteuertes_System|Event-gesteuerte Systeme]] oder [[Callback|Callbacks]].
- **Beispiel / Code:** ```java
// Beispiel für asynchrone Anbindung in einer GUI
button.addActionListener(e -> {
    new Thread(() -> {
        logic.executeLongRunningOperation();
        SwingUtilities.invokeLater(() -> updateUI());
    }).start();
});
```
