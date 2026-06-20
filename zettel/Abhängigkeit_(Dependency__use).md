---
id: 29d7c645-4bc3-5c84-a51c-5aeb4ff6024f
title: "Abhängigkeit (Dependency / <<use>>)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_5
  - draft
source: "Kapitel 5: Objektorientierung – Komposition, Aggregation und Assoziation"
---

# [[Abhängigkeit (Dependency / <<use>>)]]

- **Kernkonzept:** Eine temporäre Beziehung (gestrichelter Pfeil). Zeigt an, dass eine Klasse eine andere temporär nutzt (z. B. als Methodenparameter oder lokales Objekt), ohne eine dauerhafte Assoziation (Instanzvariable) zu halten.
- **Nutzen & Zweck:** Eine temporäre Beziehung (gestrichelter Pfeil). Zeigt an, dass eine Klasse eine andere temporär nutzt (z. B. als Methodenparameter oder lokales Objekt), ohne eine dauerhafte Assoziation (Instanzvariable) zu halten.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
public int leistungsprognose(Date datum) {
    // Temporäre Nutzung von Date; Dependency <<use>> auf Date
}
```
