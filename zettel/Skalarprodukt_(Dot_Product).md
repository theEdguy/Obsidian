---
id: f553950b-b3cd-5074-a11c-a162b7e22580
title: "Skalarprodukt (Dot Product)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_1
  - draft
source: "Kapitel 1: Mathematische und geometrische Grundlagen"
---

# [[Skalarprodukt (Dot Product)]]

- **Kernkonzept:** Für Vektoren a, b ist a · b = a_x * b_x + a_y * b_y + a_z * b_z = |a| * |b| * cos(alpha). Haupteigenschaften: Orthogonale Vektoren haben ein Skalarprodukt von 0. Wird zur Berechnung des Kosinus des Winkels zwischen Vektoren und zur Bestimmung des Reflexionsvektors r = v - 2(v · n)n genutzt (wobei n der normalisierte Oberflächennormalenvektor ist).
- **Nutzen & Zweck:** Für Vektoren a, b ist a · b = a_x * b_x + a_y * b_y + a_z * b_z = |a| * |b| * cos(alpha). Haupteigenschaften: Orthogonale Vektoren haben ein Skalarprodukt von 0. Wird zur Berechnung des Kosinus des Winkels zwischen Vektoren und zur Bestimmung des Reflexionsvektors r = v - 2(v · n)n genutzt (wobei n der normalisierte Oberflächennormalenvektor ist).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Vector3df v = {1.0f, 0.0f, -1.0f};
Vector3df n = {0.0f, 0.0f, 1.0f}; // normalisiert
v.normalize();
Vector3df r = v.get_reflective(n); // r = v - 2 * (v * n) * n
```
