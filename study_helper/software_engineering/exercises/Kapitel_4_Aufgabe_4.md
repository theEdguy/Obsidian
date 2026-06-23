---
id: 7ff9f7af-b256-5eea-8f7b-c25f70de9b69
title: "Kapitel_4_Aufgabe_4"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - klassendiagramm
  - constraints
  - exercise
  - draft
source: "Kapitel 4 Übung"
---

# Kapitel 4 Aufgabe 4

- **Aufgabenstellung:** Erklären Sie anhand des Beispiels einer Eiscreme-Klassifizierung (Kategorien: Milcheis, Fruchteis, Sorbet, Wassereis), wie die Constraints {disjoint, complete} wirken.
- **Lösungsweg / Musterlösung:** Wenn die Vererbung von der Basisklasse 'Speiseeis' auf die vier Unterklassen als `{disjoint, complete}` definiert ist, bedeutet dies:
- disjoint (disjunkt): Ein konkretes Eis kann nicht gleichzeitig zwei Kategorien angehören (z. B. kann es nicht zugleich Fruchteis und Milcheis sein).
- complete (vollständig): Jedes Eis auf der Welt muss sich in mindestens eine dieser vier Kategorien einordnen lassen. Es gibt kein Speiseeis außerhalb dieser Klassifizierung.
- **Theoretischer Bezug:** [[Kapitel_4__Objektorientierung_–_Vererbung]]
- **Stolpersteine / Fehlerquellen:** Verwechslung der Begriffe: complete bedeutet Vollständigkeit der Unterklassen (keine Reste), disjoint bedeutet Überschneidungsfreiheit.
