---
id: 797b54a5-0f9e-5cd1-a8c8-6662ffd34a50
title: "PDF-Grafikbefehle"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Bildrepräsentation"
---

# [[PDF-Grafikbefehle]]

- **Kernkonzept:** Im Content-Stream einer PDF-Seite definieren ASCII-Operatoren die Geometrie und Farbgebung: 'm' (Startpunkt setzen/moveTo), 'l' (Linie zu Punkt/lineTo), 'S' (Pfad zeichnen/Stroke), 'w' (Linienstärke), 'RG'/'rg' (Strich-/Füllfarbe in RGB), 're' (Rechteck definieren), 'B' (Füllen und Zeichnen/Fill & Stroke).
- **Nutzen & Zweck:** Im Content-Stream einer PDF-Seite definieren ASCII-Operatoren die Geometrie und Farbgebung: 'm' (Startpunkt setzen/moveTo), 'l' (Linie zu Punkt/lineTo), 'S' (Pfad zeichnen/Stroke), 'w' (Linienstärke), 'RG'/'rg' (Strich-/Füllfarbe in RGB), 're' (Rechteck definieren), 'B' (Füllen und Zeichnen/Fill & Stroke).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
150 250 m
150 350 l
S
1.0 0.0 0.0 RG
0.5 0.75 1.0 rg
200 300 50 75 re
B
```
