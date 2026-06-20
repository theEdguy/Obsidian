---
id: 8f8f74a2-698f-559f-ae20-56d2b11074c3
title: "Gooch Shading (Kalt-zu-Warm)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_9
  - draft
source: "Kapitel 9: Schattierung von Oberflächen"
---

# [[Gooch Shading (Kalt-zu-Warm)]]

- **Kernkonzept:** Ein künstlerisches Schattierungsverfahren (Non-Photorealistic Rendering) für technische Zeichnungen. Anstatt abgewandte Seiten schwarz zu zeichnen, wird zwischen einer kalten Farbe c_c (z. B. Blau) und einer warmen Farbe c_w (z. B. Orange) interpoliert, basierend auf dem Kosinus des Winkels zwischen Normalenvektor n und Lichtrichtung l: k_w = (1 + n · l) / 2. Die Pixelfarbe ergibt sich als c = k_w * c_w + (1 - k_w) * c_c.
- **Nutzen & Zweck:** Ein künstlerisches Schattierungsverfahren (Non-Photorealistic Rendering) für technische Zeichnungen. Anstatt abgewandte Seiten schwarz zu zeichnen, wird zwischen einer kalten Farbe c_c (z. B. Blau) und einer warmen Farbe c_w (z. B. Orange) interpoliert, basierend auf dem Kosinus des Winkels zwischen Normalenvektor n und Lichtrichtung l: k_w = (1 + n · l) / 2. Die Pixelfarbe ergibt sich als c = k_w * c_w + (1 - k_w) * c_c.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
float kw = (1.0 + dot(normal, lightdir)) / 2.0;
vec3 color = kw * warmColor + (1.0 - kw) * coolColor;
```
