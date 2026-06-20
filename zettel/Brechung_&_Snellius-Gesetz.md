---
id: ad2d471f-5658-5265-8d5b-b40ff7cce1d2
title: "Brechung & Snellius-Gesetz"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Raytracing"
---

# [[Brechung & Snellius-Gesetz]]

- **Kernkonzept:** Tritt beim Übergang eines Strahls in ein anderes Medium auf: eta_1 * sin(theta) = eta_2 * sin(phi). Die Richtung des gebrochenen Strahls t berechnet sich als t = n*d - (n*(d · n) + sqrt(1 - n^2*(1 - (d · n)^2)))*n mit n = eta_1/eta_2. Wenn der Term unter der Wurzel (die Diskriminante) negativ wird, tritt Totalreflexion auf (keine Brechung).
- **Nutzen & Zweck:** Tritt beim Übergang eines Strahls in ein anderes Medium auf: eta_1 * sin(theta) = eta_2 * sin(phi). Die Richtung des gebrochenen Strahls t berechnet sich als t = n*d - (n*(d · n) + sqrt(1 - n^2*(1 - (d · n)^2)))*n mit n = eta_1/eta_2. Wenn der Term unter der Wurzel (die Diskriminante) negativ wird, tritt Totalreflexion auf (keine Brechung).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Vector3df t;
bool refract_exists = refract(eta1/eta2, normal, direction, t);
```
