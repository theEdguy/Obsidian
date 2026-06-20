---
id: 7a5a2538-79b7-5100-aeb6-7b2315d81101
title: "Ordered Constraint (UML)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Objektorientierung – Komposition, Aggregation und Assoziation"
---

# [[Ordered Constraint (UML)]]

- **Kernkonzept:** Constraint, das vorgibt, dass die verknüpften Objekte an einem Assoziationsende in einer festen, definierten Reihenfolge vorliegen müssen (z. B. sortierte Listen), dargestellt durch `{ordered}`.
- **Nutzen & Zweck:** Constraint, das vorgibt, dass die verknüpften Objekte an einem Assoziationsende in einer festen, definierten Reihenfolge vorliegen müssen (z. B. sortierte Listen), dargestellt durch `{ordered}`.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
private List<Mitglied> mitglieder = new ArrayList<>(); // Die Reihenfolge der Liste ist relevant
```
