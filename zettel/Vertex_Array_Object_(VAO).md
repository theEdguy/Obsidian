---
id: eb853988-3f6a-52ab-8448-a1a8b28261ae
title: "Vertex Array Object (VAO)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_7
  - draft
source: "Kapitel 7: OpenGL"
---

# [[Vertex Array Object (VAO)]]

- **Kernkonzept:** Ein Zustandsobjekt, das alle Einstellungen für Vertex-Layouts und Pufferbindungen speichert. Es kapselt die glVertexAttribPointer-Konfigurationen und die Aktivierung von Attributindizes, wodurch das Umschalten zwischen verschiedenen Modellen mit einem einzigen Aufruf möglich wird.
- **Nutzen & Zweck:** Ein Zustandsobjekt, das alle Einstellungen für Vertex-Layouts und Pufferbindungen speichert. Es kapselt die glVertexAttribPointer-Konfigurationen und die Aktivierung von Attributindizes, wodurch das Umschalten zwischen verschiedenen Modellen mit einem einzigen Aufruf möglich wird.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
GLuint VAO;
glGenVertexArrays(1, &VAO);
glBindVertexArray(VAO);
// Danach glVertexAttribPointer-Aufrufe tätigen...
```
