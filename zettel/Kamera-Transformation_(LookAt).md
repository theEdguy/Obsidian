---
id: 76786b16-3a07-5072-bab4-a282cd5bb90e
title: "Kamera-Transformation (LookAt)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Projektionen"
---

# [[Kamera-Transformation (LookAt)]]

- **Kernkonzept:** Verschiebt die Szene so, dass die Kamera im Ursprung liegt und blickt. Gegeben: Augenpunkt e, Blickrichtung g, Up-Vektor t. Orthonormalbasis berechnen: w = -g / |g| (z-Achse der Kamera zeigt nach hinten), u = (t x w) / |t x w| (x-Achse der Kamera zeigt nach rechts), v = w x u (y-Achse der Kamera zeigt nach oben). LookAt-Matrix ist M = R · T mit Rotation R (u, v, w in Zeilen) und Translation T (um -e).
- **Nutzen & Zweck:** Verschiebt die Szene so, dass die Kamera im Ursprung liegt und blickt. Gegeben: Augenpunkt e, Blickrichtung g, Up-Vektor t. Orthonormalbasis berechnen: w = -g / |g| (z-Achse der Kamera zeigt nach hinten), u = (t x w) / |t x w| (x-Achse der Kamera zeigt nach rechts), v = w x u (y-Achse der Kamera zeigt nach oben). LookAt-Matrix ist M = R · T mit Rotation R (u, v, w in Zeilen) und Translation T (um -e).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
