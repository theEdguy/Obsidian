---
id: d0331427-60a3-5eea-9975-a0e78a20b4a2
title: "glDrawArrays"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[glDrawArrays]]

- **Kernkonzept:** Rendert geometrische Primitive aus dem aktiven Vertex-Array-Zustand. Parameter:
1. mode: Primitiv-Typ (z.B. GL_TRIANGLES, GL_LINES)
2. first: Startindex im Array
3. count: Anzahl der zu zeichnenden Vertices (nicht Dreiecke; z.B. 3 Vertices pro Dreieck).
- **Nutzen & Zweck:** Rendert geometrische Primitive aus dem aktiven Vertex-Array-Zustand. Parameter:
1. mode: Primitiv-Typ (z.B. GL_TRIANGLES, GL_LINES)
2. first: Startindex im Array
3. count: Anzahl der zu zeichnenden Vertices (nicht Dreiecke; z.B. 3 Vertices pro Dreieck).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
glDrawArrays(GL_TRIANGLES, 0, 9); // Zeichnet die ersten drei Dreiecke (9 Eckpunkte)
```
