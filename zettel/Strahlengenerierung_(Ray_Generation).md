---
id: 9c8eb7bc-9c43-5136-a392-5805240ba5df
title: "Strahlengenerierung (Ray Generation)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Raytracing"
---

# [[Strahlengenerierung (Ray Generation)]]

- **Kernkonzept:** Erzeugung des Sehstrahls für ein Pixel (i, j) mit Koordinaten (p_u, p_v). Bei Parallelprojektion sind alle Strahlen parallel (ray.origin = e + p_u*u + p_v*v, ray.direction = -w). Bei Zentralprojektion starten alle Strahlen im Augenpunkt e (ray.origin = e, ray.direction = -d*w + p_u*u + p_v*v, mit Bildebenenabstand d).
- **Nutzen & Zweck:** Erzeugung des Sehstrahls für ein Pixel (i, j) mit Koordinaten (p_u, p_v). Bei Parallelprojektion sind alle Strahlen parallel (ray.origin = e + p_u*u + p_v*v, ray.direction = -w). Bei Zentralprojektion starten alle Strahlen im Augenpunkt e (ray.origin = e, ray.direction = -d*w + p_u*u + p_v*v, mit Bildebenenabstand d).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Ray3df get_ray_perspective(float i, float j, Vector3df e, Vector3df u, Vector3df v, Vector3df w, float d, float l, float r, float b, float t, float nx, float ny) {
  float pu = l + (r - l) * (i + 0.5f) / nx;
  float pv = b + (t - b) * (j + 0.5f) / ny;
  Vector3df dir = -d * w + pu * u + pv * v;
  dir.normalize();
  return Ray3df{e, dir};
}
```
