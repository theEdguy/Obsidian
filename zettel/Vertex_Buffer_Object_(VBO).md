---
id: 84287ab3-d530-5a0b-8802-67c700df9975
title: "Vertex Buffer Object (VBO)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[Vertex Buffer Object (VBO)]]

- **Kernkonzept:** Ein Speicherpuffer im Grafikspeicher (GPU) zur Speicherung von Vertex-Attributdaten (z. B. Positionen, Farben, Normalen, Texturkoordinaten). Wird über glGenBuffers erzeugt und an das Target GL_ARRAY_BUFFER gebunden.
- **Nutzen & Zweck:** Ein Speicherpuffer im Grafikspeicher (GPU) zur Speicherung von Vertex-Attributdaten (z. B. Positionen, Farben, Normalen, Texturkoordinaten). Wird über glGenBuffers erzeugt und an das Target GL_ARRAY_BUFFER gebunden.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
GLuint VBO;
glGenBuffers(1, &VBO);
glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
```
