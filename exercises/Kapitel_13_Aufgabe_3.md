---
id: 08d64d13-ab5e-5f62-9973-2a7503161528
title: "Kapitel_13_Aufgabe_3"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - sequenzdiagramm
  - recursion
  - grasp
  - exercise
  - draft
source: "Kapitel 13 Übung"
---

# Kapitel 13 Aufgabe 3

- **Aufgabenstellung:** Ein Knoten in einem Graphen besitzt eine Methode `pathExists(Node target, Set<Node> visited)`. Skizzieren Sie das Sequenzdiagramm für einen erfolgreichen rekursiven Aufruf, bei dem ein Nachbar besucht wird, der noch nicht in `visited` enthalten ist.
- **Lösungsweg / Musterlösung:** 1. Der Client ruft `n1:Node.pathExists(target, visited)` auf.
2. `n1` fügt sich selbst der Menge `visited` hinzu: `visited.add(n1)`.
3. `n1` prüft, ob `n1 == target` (hier false).
4. `n1` holt seine Nachbarn und iteriert. Für einen unbesuchten Nachbarn `n2` ruft `n1` auf: `n2.pathExists(target, visited)` innerhalb eines `loop`- und `alt`-Fragments.
5. `n2` führt dieselben Schritte aus und gibt schließlich `true` zurück.
6. `n1` erhält `true` und reicht dieses Ergebnis an den Client weiter.
- **Theoretischer Bezug:** [[Kapitel_13__Interaktionsdiagramme_und_GRASP-Verantwortlichkeiten]]
- **Stolpersteine / Fehlerquellen:** Vergessen der Rekursion im Sequenzdiagramm (Pfeil von `n1` auf eine andere Instanz `n2` desselben Typs `Node`). Das fehlerhafte Zeichnen der Parameterübergabe.
