---
id: b299ec85-973d-528b-b78e-dbec1d80bd2a
title: "OpenGL Texturfilterung & Wrapping"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_8
  - draft
source: "Kapitel 8: Texturabbildungen"
---

# [[OpenGL Texturfilterung & Wrapping]]

- **Kernkonzept:** Wrapping bestimmt, wie Texturen außerhalb des Bereichs [0, 1] wiederholt oder abgeschnitten werden (GL_TEXTURE_WRAP_S, GL_TEXTURE_WRAP_T: GL_REPEAT, GL_CLAMP_TO_EDGE). Filtering bestimmt das Verhalten bei Skalierung (GL_TEXTURE_MIN_FILTER, GL_TEXTURE_MAG_FILTER): GL_NEAREST (nächstgelegener Texel, pixelig) und GL_LINEAR (bilineare Interpolation, weich).
- **Nutzen & Zweck:** Wrapping bestimmt, wie Texturen außerhalb des Bereichs [0, 1] wiederholt oder abgeschnitten werden (GL_TEXTURE_WRAP_S, GL_TEXTURE_WRAP_T: GL_REPEAT, GL_CLAMP_TO_EDGE). Filtering bestimmt das Verhalten bei Skalierung (GL_TEXTURE_MIN_FILTER, GL_TEXTURE_MAG_FILTER): GL_NEAREST (nächstgelegener Texel, pixelig) und GL_LINEAR (bilineare Interpolation, weich).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
```
