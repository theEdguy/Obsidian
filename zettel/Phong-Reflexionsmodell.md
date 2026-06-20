---
id: bad64294-a6bb-5616-96de-01cac0f37fce
title: "Phong-Reflexionsmodell"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_9
  - draft
source: "Kapitel 9: Schattierung von Oberflächen"
---

# [[Phong-Reflexionsmodell]]

- **Kernkonzept:** Ein lokales Beleuchtungsmodell. Die Pixelfarbe berechnet sich aus ambientem, diffusem (Lambert) und spiegelndem (specular) Anteil: c = k_a * I_a + k_d * I_d * max(0, n · l) + k_s * I_s * max(0, r · e)^p. Hierbei ist r der Reflexionsrichtungsvektor des Lichts, e der Blickrichtungsvektor (beide normalisiert) und p der Phong-Exponent (Steilheit des Glanzlichts).
- **Nutzen & Zweck:** Ein lokales Beleuchtungsmodell. Die Pixelfarbe berechnet sich aus ambientem, diffusem (Lambert) und spiegelndem (specular) Anteil: c = k_a * I_a + k_d * I_d * max(0, n · l) + k_s * I_s * max(0, r · e)^p. Hierbei ist r der Reflexionsrichtungsvektor des Lichts, e der Blickrichtungsvektor (beide normalisiert) und p der Phong-Exponent (Steilheit des Glanzlichts).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
