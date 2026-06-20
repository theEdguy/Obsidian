---
id: 0aec4d99-ede7-5158-a32b-0e53f93b3ff0
title: "Schlicksche Approximation"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Raytracing"
---

# [[Schlicksche Approximation]]

- **Kernkonzept:** Eine Näherungsformel zur Berechnung des reflexiven Anteils R(theta) eines transparenten Materials in Abhängigkeit vom Einfallswinkel. R(theta) = R_0 + (1 - R_0)*(1 - cos(theta))^5 mit R_0 = ((eta_1 - eta_2)/(eta_1 + eta_2))^2 und cos(theta) = -d · n. Der gebrochene Anteil ist 1 - R(theta).
- **Nutzen & Zweck:** Eine Näherungsformel zur Berechnung des reflexiven Anteils R(theta) eines transparenten Materials in Abhängigkeit vom Einfallswinkel. R(theta) = R_0 + (1 - R_0)*(1 - cos(theta))^5 mit R_0 = ((eta_1 - eta_2)/(eta_1 + eta_2))^2 und cos(theta) = -d · n. Der gebrochene Anteil ist 1 - R(theta).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
