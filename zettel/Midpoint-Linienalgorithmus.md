---
id: c7b4b63d-42a2-5533-9716-ce0dc5368a96
title: "Midpoint-Linienalgorithmus"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_6
  - draft
source: "Kapitel 6: Graphik-Pipeline & Rasterung"
---

# [[Midpoint-Linienalgorithmus]]

- **Kernkonzept:** Zeichnet Linien im Raster unter Vermeidung von Gleitkommaoperationen. Basiert auf der impliziten Geradengleichung f(x, y) = (y_0 - y_1)*x + (x_1 - x_0)*y + x_0*y_1 - x_1*y_0 = 0. Für eine Steigung m in [0, 1) wird ausgehend vom letzten Pixel (x, y) der Wert f(x + 1, y + 0.5) am Mittelpunkt evaluiert. Ist er < 0, liegt die Linie über dem Mittelpunkt (oberes Pixel wählen: y = y + 1), andernfalls das untere (y = y). Die Updates für d erfolgen rein additiv.
- **Nutzen & Zweck:** Zeichnet Linien im Raster unter Vermeidung von Gleitkommaoperationen. Basiert auf der impliziten Geradengleichung f(x, y) = (y_0 - y_1)*x + (x_1 - x_0)*y + x_0*y_1 - x_1*y_0 = 0. Für eine Steigung m in [0, 1) wird ausgehend vom letzten Pixel (x, y) der Wert f(x + 1, y + 0.5) am Mittelpunkt evaluiert. Ist er < 0, liegt die Linie über dem Mittelpunkt (oberes Pixel wählen: y = y + 1), andernfalls das untere (y = y). Die Updates für d erfolgen rein additiv.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
