---
id: cbadc3db-31df-5707-b25f-7ce6dcbd34d8
title: "Backface-Culling"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[Backface-Culling]]

- **Kernkonzept:** Zustand zur Ausblendung von Dreiecken, die der Kamera abgewandt sind. Wird mit glEnable(GL_CULL_FACE) aktiviert. Die Eckenreihenfolge der projizierten Dreiecke im 2D-Bildraum bestimmt, ob sie gegen den Uhrzeigersinn (GL_CCW) oder im Uhrzeigersinn (GL_CW) orientiert sind. Mittels glFrontFace und glCullFace wird konfiguriert, welche Seiten verworfen werden.
- **Nutzen & Zweck:** Zustand zur Ausblendung von Dreiecken, die der Kamera abgewandt sind. Wird mit glEnable(GL_CULL_FACE) aktiviert. Die Eckenreihenfolge der projizierten Dreiecke im 2D-Bildraum bestimmt, ob sie gegen den Uhrzeigersinn (GL_CCW) oder im Uhrzeigersinn (GL_CW) orientiert sind. Mittels glFrontFace und glCullFace wird konfiguriert, welche Seiten verworfen werden.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
glEnable(GL_CULL_FACE);
glFrontFace(GL_CCW); // Gegenuhrzeigersinn ist Vorderseite
glCullFace(GL_BACK);   // Rückseiten verwerfen
```
