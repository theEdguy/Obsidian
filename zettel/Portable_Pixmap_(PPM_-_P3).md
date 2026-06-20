---
id: 47bd3b63-a514-531f-9f3a-fcfa96b58e73
title: "Portable Pixmap (PPM - P3)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Bildrepräsentation"
---

# [[Portable Pixmap (PPM - P3)]]

- **Kernkonzept:** Ein textbasiertes (ASCII), unkomprimiertes Format zur Speicherung von RGB-Rastergrafiken. Die Datei beginnt mit der Magic Number 'P3', gefolgt von Breite und Höhe (in Pixeln) und dem maximalen Farbwert je Kanal. Die Pixel werden zeilenweise von oben links nach unten rechts als RGB-Tripel aufgeschrieben.
- **Nutzen & Zweck:** Ein textbasiertes (ASCII), unkomprimiertes Format zur Speicherung von RGB-Rastergrafiken. Die Datei beginnt mit der Magic Number 'P3', gefolgt von Breite und Höhe (in Pixeln) und dem maximalen Farbwert je Kanal. Die Pixel werden zeilenweise von oben links nach unten rechts als RGB-Tripel aufgeschrieben.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
P3
3 2
255
255 0 0   0 255 0   0 0 255
255 255 255   128 128 128   0 0 0
```
