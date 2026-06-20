---
id: a3d958cf-3bb6-5bd2-9592-941828348a95
title: "GLSL Textur-Shader"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_8
  - draft
source: "Kapitel 8: Texturabbildungen"
---

# [[GLSL Textur-Shader]]

- **Kernkonzept:** Um Texturdaten im Fragment-Shader zu nutzen, wird eine Variable uniform sampler2D texturedata deklariert. Über die Funktion texture(texturedata, texCoord) wird die RGB(A)-Farbe an der Stelle texCoord (vec2) ausgelesen.
- **Nutzen & Zweck:** Um Texturdaten im Fragment-Shader zu nutzen, wird eine Variable uniform sampler2D texturedata deklariert. Über die Funktion texture(texturedata, texCoord) wird die RGB(A)-Farbe an der Stelle texCoord (vec2) ausgelesen.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
#version 330 core
in vec2 texturecoordout;
out vec4 FragColor;
uniform sampler2D texturedata;
void main() {
  FragColor = texture(texturedata, texturecoordout);
}
```
