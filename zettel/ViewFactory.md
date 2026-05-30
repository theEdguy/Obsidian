---
id: f9b90b36-cf13-4578-a2b1-b07442adc01f
title: "ViewFactory"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - erzeugungsmuster
  - gui_design
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[ViewFactory]]

- **Kernkonzept:** Eine [[ViewFactory]] ist ein [[Erzeugungsmuster|Erzeugungsmuster]], das die [[Erstellung]] von [[View|Views]] basierend auf dem aktuellen [[Zustand]] oder [[Kontext]] zentralisiert. Sie trennt die [[Logik]] der [[View]]-Erzeugung von der [[Logik]] der [[View]]-Nutzung.
- **Nutzen & Zweck:** Sie löst das [[Problem]] der manuellen [[View]]-Erstellung in [[GUI]]s mit vielen [[Zustand|Zuständen]], indem sie eine zentrale [[Schnittstelle]] für die [[Erzeugung]] bereitstellt und die [[Wiederverwendbarkeit]] von [[View|Views]] fördert.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache Anwendungen mit wenigen [[View|Views]], da der [[Overhead]] der [[Factory]]-Implementierung den Nutzen übersteigt. Alternativen wie direkte [[Instanzierung]] können hier effizienter sein.
- **Beispiel / Code:** ```java
// Beispiel für eine ViewFactory
public class ViewFactory {
    public View mkView(State state) {
        switch (state) {
            case LOGIN: return new LoginView();
            case DASHBOARD: return new DashboardView();
            default: throw new IllegalArgumentException("Unbekannter Zustand");
        }
    }
}
```
