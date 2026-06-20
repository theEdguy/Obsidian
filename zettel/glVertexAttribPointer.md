---
id: 96605b4e-b654-58c5-b936-8899d2f20486
title: "glVertexAttribPointer"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[glVertexAttribPointer]]

- **Kernkonzept:** Spezifiziert das Format der Vertex-Attribute im gebundenen VBO. Parameter:
1. index: layout-Location im Shader
2. size: Anzahl der Komponenten (z. B. 2 für 2D-Punkt, 3 für RGB-Farbe)
3. type: Datentyp (meist GL_FLOAT)
4. normalized: Sollen Werte normalisiert werden (GL_FALSE)
5. stride: Byte-Abstand zwischen aufeinanderfolgenden Attributen
6. pointer: Offset des ersten Werts im Puffer.
- **Nutzen & Zweck:** Spezifiziert das Format der Vertex-Attribute im gebundenen VBO. Parameter:
1. index: layout-Location im Shader
2. size: Anzahl der Komponenten (z. B. 2 für 2D-Punkt, 3 für RGB-Farbe)
3. type: Datentyp (meist GL_FLOAT)
4. normalized: Sollen Werte normalisiert werden (GL_FALSE)
5. stride: Byte-Abstand zwischen aufeinanderfolgenden Attributen
6. pointer: Offset des ersten Werts im Puffer.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
glVertexAttribPointer(1, 3, GL_FLOAT, GL_FALSE, 6 * sizeof(float), (void*)(3 * sizeof(float)));
glEnableVertexAttribArray(1);
```
