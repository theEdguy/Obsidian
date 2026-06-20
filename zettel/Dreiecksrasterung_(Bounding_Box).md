---
id: 06b52cb7-115a-5867-b3c7-b73a497023e1
title: "Dreiecksrasterung (Bounding Box)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_6
  - draft
source: "Kapitel 6: Graphik-Pipeline & Rasterung"
---

# [[Dreiecksrasterung (Bounding Box)]]

- **Kernkonzept:** Um ein Dreieck mit den Ecken p0, p1, p2 zu zeichnen, berechnet man dessen achsenparallele Bounding-Box (xmin = floor(min(x0,x1,x2)), etc.). Über alle Pixel in dieser Box wird iteriert und geprüft, ob die baryzentrischen Koordinaten u, v, w alle >= 0 sind. Wenn ja, wird das Pixel gezeichnet. Attribute wie Farbe werden über c = u*c0 + v*c1 + w*c2 interpoliert.
- **Nutzen & Zweck:** Um ein Dreieck mit den Ecken p0, p1, p2 zu zeichnen, berechnet man dessen achsenparallele Bounding-Box (xmin = floor(min(x0,x1,x2)), etc.). Über alle Pixel in dieser Box wird iteriert und geprüft, ob die baryzentrischen Koordinaten u, v, w alle >= 0 sind. Wenn ja, wird das Pixel gezeichnet. Attribute wie Farbe werden über c = u*c0 + v*c1 + w*c2 interpoliert.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
