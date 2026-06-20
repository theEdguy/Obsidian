---
id: 245b61eb-5f95-5886-acdd-3b6dfe71e5dd
title: "Schattenakne & Epsilon-Offset"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Raytracing"
---

# [[Schattenakne & Epsilon-Offset]]

- **Kernkonzept:** Visueller Fehler (dunkle Punkte/Muster auf beleuchteten Flächen), der durch numerische Ungenauigkeiten entsteht. Wenn der Schnittpunkt p eines Strahls berechnet wird, kann er leicht unter/hinter der Oberfläche liegen. Ein neuer Schatten- oder Reflexionsstrahl schneidet dann sofort wieder dasselbe Objekt. Lösung: Startpunkt um epsilon * n in Normalenrichtung verschieben (p_neu = p + epsilon * n).
- **Nutzen & Zweck:** Visueller Fehler (dunkle Punkte/Muster auf beleuchteten Flächen), der durch numerische Ungenauigkeiten entsteht. Wenn der Schnittpunkt p eines Strahls berechnet wird, kann er leicht unter/hinter der Oberfläche liegen. Ein neuer Schatten- oder Reflexionsstrahl schneidet dann sofort wieder dasselbe Objekt. Lösung: Startpunkt um epsilon * n in Normalenrichtung verschieben (p_neu = p + epsilon * n).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Vector3df shadow_ray_origin = hit_point + 1e-4f * normal;
```
