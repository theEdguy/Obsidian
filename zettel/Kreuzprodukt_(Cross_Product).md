---
id: bbbe0d0a-0ab6-56d3-a25b-869857c4bb62
title: "Kreuzprodukt (Cross Product)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_1
  - draft
source: "Kapitel 1: Mathematische und geometrische Grundlagen"
---

# [[Kreuzprodukt (Cross Product)]]

- **Kernkonzept:** Nur für 3D-Vektoren definiert: a x b = (a_y*b_z - a_z*b_y, a_z*b_x - a_x*b_z, a_x*b_y - a_y*b_x). Das Ergebnis ist ein Vektor, der orthogonal auf der durch a und b aufgespannten Ebene steht (Rechte-Hand-Regel). Seine Länge |a x b| = |a| * |b| * sin(alpha) entspricht der Fläche des aufgespannten Parallelogramms (bzw. doppelte Dreiecksfläche). Es ist antikommutativ: a x b = -(b x a).
- **Nutzen & Zweck:** Nur für 3D-Vektoren definiert: a x b = (a_y*b_z - a_z*b_y, a_z*b_x - a_x*b_z, a_x*b_y - a_y*b_x). Das Ergebnis ist ein Vektor, der orthogonal auf der durch a und b aufgespannten Ebene steht (Rechte-Hand-Regel). Seine Länge |a x b| = |a| * |b| * sin(alpha) entspricht der Fläche des aufgespannten Parallelogramms (bzw. doppelte Dreiecksfläche). Es ist antikommutativ: a x b = -(b x a).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Vector3df a = {1.0f, 0.0f, 0.0f};
Vector3df b = {0.0f, 1.0f, 0.0f};
Vector3df c = a.cross_product(b); // c = {0.0f, 0.0f, 1.0f}
```
