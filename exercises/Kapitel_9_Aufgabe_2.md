---
id: 96e23027-4e60-50f2-b0c1-6f9e902688ac
title: "Kapitel_9_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - system_operationen
  - schnittstelle
  - aktivitaetsdiagramm
  - exercise
  - draft
source: "Kapitel 9 Übung"
---

# Kapitel 9 Aufgabe 2

- **Aufgabenstellung:** Ein Aktivitätsdiagramm zeigt den Austausch zwischen Akteur 'Kunde' und System. Der Kunde wählt 'ISBN erfassen', woraufhin das System 'Buch suchen' ausführt. Dann wählt der Kunde 'Bestätigen' und das System führt 'Buch inventarisieren' aus. Welche Systemoperationen müssen für die Schnittstelle des Systems definiert werden?
- **Lösungsweg / Musterlösung:** Es müssen zwei Systemoperationen deklariert werden:
1. `suchen(isbn: String): Buch` (wird durch 'ISBN erfassen' getriggert).
2. `inventarisieren(buchId: int): void` (wird durch 'Bestätigen' getriggert).

Erklärung: Jedes Mal, wenn der Kontrollfluss die Systemgrenze vom Akteur zum System überschreitet, wird eine Operation aufgerufen. Die Aktionen innerhalb des Systems beschreiben die Zuständigkeit der jeweiligen Operation.
- **Theoretischer Bezug:** [[Kapitel_9__Use_Cases_interpretieren]]
- **Stolpersteine / Fehlerquellen:** Das Erstellen von Operationen für Aktionen des Akteurs (z. B. `isbnErfassen()`). Die Schnittstelle enthält nur Operationen, die das *System* ausführt.
