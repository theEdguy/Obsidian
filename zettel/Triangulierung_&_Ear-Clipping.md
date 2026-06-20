---
id: cd2bf16f-8792-5fc4-8e7a-90793722422d
title: "Triangulierung & Ear-Clipping"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_1
  - draft
source: "Kapitel 1: Mathematische und geometrische Grundlagen"
---

# [[Triangulierung & Ear-Clipping]]

- **Kernkonzept:** Jedes einfache Polygon mit k Punkten lässt sich in k-2 Dreiecke zerlegen. Ein Ohr ist ein aus drei aufeinanderfolgenden Punkten gebildetes inneres Dreieck, das von keiner Kante überschnitten wird. Das Zwei-Ohren-Theorem besagt, dass jedes einfache Polygon mit mehr als drei Punkten mindestens zwei Ohren besitzt. Der Algorithmus sucht und schneidet fortlaufend Ohren ab, bis nur noch ein Dreieck übrig ist. Naive Laufzeit: O(n^3); optimierte Laufzeit: O(n^2), wenn effizient geprüft wird, ob andere Eckpunkte im Ohr liegen.
- **Nutzen & Zweck:** Jedes einfache Polygon mit k Punkten lässt sich in k-2 Dreiecke zerlegen. Ein Ohr ist ein aus drei aufeinanderfolgenden Punkten gebildetes inneres Dreieck, das von keiner Kante überschnitten wird. Das Zwei-Ohren-Theorem besagt, dass jedes einfache Polygon mit mehr als drei Punkten mindestens zwei Ohren besitzt. Der Algorithmus sucht und schneidet fortlaufend Ohren ab, bis nur noch ein Dreieck übrig ist. Naive Laufzeit: O(n^3); optimierte Laufzeit: O(n^2), wenn effizient geprüft wird, ob andere Eckpunkte im Ohr liegen.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
