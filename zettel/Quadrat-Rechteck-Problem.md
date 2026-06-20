---
id: 2ca6e160-8bca-5c7d-b8bf-38f9f4215f58
title: "Quadrat-Rechteck-Problem"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Objektorientierung – Vererbung"
---

# [[Quadrat-Rechteck-Problem]]

- **Kernkonzept:** Ein klassischer Verstoß gegen das Substitutionsprinzip: Erbt Quadrat von Rechteck, verletzt Quadrat die Rechteck-Eigenschaft (Breite und Höhe unabhängig veränderbar, z. B. stretch(w, h)), da beim Quadrat w = h gelten muss.
- **Nutzen & Zweck:** Ein klassischer Verstoß gegen das Substitutionsprinzip: Erbt Quadrat von Rechteck, verletzt Quadrat die Rechteck-Eigenschaft (Breite und Höhe unabhängig veränderbar, z. B. stretch(w, h)), da beim Quadrat w = h gelten muss.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
Rechteck r = new Quadrat(3);
r.setBreite(4);
r.setHoehe(5);
// Wenn r ein Quadrat ist, gilt nun Breite=5, Hoehe=5. Erwartet wurde aber Flaeche 20!
```
