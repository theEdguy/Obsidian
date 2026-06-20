---
id: 22ff92e4-d585-5801-a1e4-0a9262815443
title: "GLSL (OpenGL Shading Language)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[GLSL (OpenGL Shading Language)]]

- **Kernkonzept:** Die Programmiersprache für OpenGL-Shader. Läuft direkt auf der GPU. Variablen werden mittels 'in' (Eingabe) und 'out' (Ausgabe) deklariert. Der Vertex-Shader transformiert Vertices und schreibt in 'gl_Position'. Der Fragment-Shader schreibt die Pixelfarbe in ein definiertes Ausgabe-Objekt (z. B. 'FragColor'). Unterstützt Swizzling (z. B. 'color.rgb' oder 'pos.xy'). Keine Rekursion.
- **Nutzen & Zweck:** Die Programmiersprache für OpenGL-Shader. Läuft direkt auf der GPU. Variablen werden mittels 'in' (Eingabe) und 'out' (Ausgabe) deklariert. Der Vertex-Shader transformiert Vertices und schreibt in 'gl_Position'. Der Fragment-Shader schreibt die Pixelfarbe in ein definiertes Ausgabe-Objekt (z. B. 'FragColor'). Unterstützt Swizzling (z. B. 'color.rgb' oder 'pos.xy'). Keine Rekursion.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
#version 330 core
layout (location = 0) in vec3 pos;
layout (location = 1) in vec3 color;
out vec3 out_color;
void main() {
  out_color = color;
  gl_Position = vec4(pos, 1.0);
}
```
