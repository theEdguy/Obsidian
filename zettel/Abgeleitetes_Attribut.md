---
id: 24115468-b5f7-41fe-8e5d-4d9d2d28f9c4
title: "Abgeleitetes_Attribut"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - datenmodellierung
  - draft
source: "SWE Slides (Folien 76-90)"
---

# [[Abgeleitetes_Attribut]]

- **Kernkonzept:** Ein [[Attribut]] in [[UML]], dessen [[Wert]] aus anderen [[Attribut|Attributen]] oder [[Information|Informationen]] berechnet wird und nicht gespeichert werden muss. Wird mit einem `/` vor dem [[Attributname|Attributnamen]] gekennzeichnet.
- **Nutzen & Zweck:** Reduziert [[Redundanz]] und stellt sicher, dass [[Daten]] konsistent bleiben. Ermöglicht die [[Abstraktion]] von [[Berechnung|Berechnungen]], die aus anderen [[Attribut|Attributen]] abgeleitet werden können.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn die [[Berechnung]] komplex oder rechenintensiv ist. Kann zu [[Performance-Problem|Performance-Problemen]] führen, wenn häufig auf das [[Attribut]] zugegriffen wird. Sollte nicht für [[Daten]] verwendet werden, die persistent gespeichert werden müssen.
- **Beispiel / Code:** ```uml
class Rechteck {
    +a: Integer
    +b: Integer
    +/flaeche: Integer {derived}
}

// Implementierung
public int getFlaeche() {
    return a * b;
}
```
