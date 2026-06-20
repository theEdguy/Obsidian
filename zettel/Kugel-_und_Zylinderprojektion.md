---
id: abcf4269-a593-5895-8099-91749506ef44
title: "Kugel- und Zylinderprojektion"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_8
  - draft
source: "Kapitel 8: Texturabbildungen"
---

# [[Kugel- und Zylinderprojektion]]

- **Kernkonzept:** Zylindrische Projektion wickelt die Textur um die z-Achse: u = 1/(2*PI) * (PI + atan2(y, x)), v = 0.5 * (z + 1) (für z in [-1, 1]). Sphärische Projektion bildet Koordinaten auf eine Kugel mit Radius 1 ab: u = 1/(2*PI) * (PI + atan2(y, x)), v = 1/PI * (PI - acos(z / |p|)) (wobei |p| die Länge des 3D-Positionsvektors ist).
- **Nutzen & Zweck:** Zylindrische Projektion wickelt die Textur um die z-Achse: u = 1/(2*PI) * (PI + atan2(y, x)), v = 0.5 * (z + 1) (für z in [-1, 1]). Sphärische Projektion bildet Koordinaten auf eine Kugel mit Radius 1 ab: u = 1/(2*PI) * (PI + atan2(y, x)), v = 1/PI * (PI - acos(z / |p|)) (wobei |p| die Länge des 3D-Positionsvektors ist).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
