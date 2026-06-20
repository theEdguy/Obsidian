---
id: a1af10c7-47e2-5609-b5ae-137405465bcd
title: "Gouraud Shading"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_9
  - draft
source: "Kapitel 9: Schattierung von Oberflächen"
---

# [[Gouraud Shading]]

- **Kernkonzept:** Schattierungsmethode, bei der die Beleuchtungsberechnung an den Eckpunkten (Vertices) des Polygons im Vertex-Shader durchgeführt wird. Die resultierenden Eckpunktfarben werden während der Rasterisierung linear über die Fläche interpoliert. Vorteil: Schnelle Berechnung. Nachteil: Glanzlichter (specular highlights) gehen verloren, wenn sie in der Mitte des Polygons liegen, oder werden unnatürlich verzerrt.
- **Nutzen & Zweck:** Schattierungsmethode, bei der die Beleuchtungsberechnung an den Eckpunkten (Vertices) des Polygons im Vertex-Shader durchgeführt wird. Die resultierenden Eckpunktfarben werden während der Rasterisierung linear über die Fläche interpoliert. Vorteil: Schnelle Berechnung. Nachteil: Glanzlichter (specular highlights) gehen verloren, wenn sie in der Mitte des Polygons liegen, oder werden unnatürlich verzerrt.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
