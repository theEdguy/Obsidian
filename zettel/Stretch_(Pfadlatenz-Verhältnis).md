---
id: 4bb82910-4f52-5cc5-8fcc-9d600c871bdd
title: "Stretch (Pfadlatenz-Verhältnis)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Kommunikation"
---

# [[Stretch (Pfadlatenz-Verhältnis)]]

- **Kernkonzept:** Verhältnis der Gesamtlatenz/Kosten einer Kommunikation über das Overlay-Netzwerk zu den Kosten über den optimalen physischen Routing-Weg im darunterliegenden IP-Netzwerk: Stretch = Kosten(Overlay) / Kosten(Physisch).
- **Nutzen & Zweck:** Verhältnis der Gesamtlatenz/Kosten einer Kommunikation über das Overlay-Netzwerk zu den Kosten über den optimalen physischen Routing-Weg im darunterliegenden IP-Netzwerk: Stretch = Kosten(Overlay) / Kosten(Physisch).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# Beispiel aus SS25:
# Kosten über Overlay A->B->C->D = 10 + 16 + 14 = 40
# Bester physischer Weg A->Ra->Rb->Rd->D = 1 + 8 + 10 + 1 = 20
# Stretch = 40 / 20 = 2.0
```
