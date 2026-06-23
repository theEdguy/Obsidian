---
id: 9ae33ffb-d403-5dcf-8485-164fbed1cd95
title: "Kapitel_16_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - aktivitaetsdiagramm
  - persistenz
  - dictionary
  - exercise
  - draft
source: "Kapitel 16 Übung"
---

# Kapitel 16 Aufgabe 2

- **Aufgabenstellung:** Skizzieren Sie ein Aktivitätsdiagramm für den Use Case 'Adresse bearbeiten'. Das System nutzt ein Dictionary, das die Daten in Blöcken eines B+-Baums verwaltet. Berücksichtigen Sie die Interaktion zwischen UI-Controller, Dictionary-Komponente und dem Key-Value-Store.
- **Lösungsweg / Musterlösung:** Das Aktivitätsdiagramm enthält:
1. Drei Swimlanes: `Controller`, `Dictionary` und `Store`.
2. Der Fluss startet im `Controller` mit der Aktion 'Eingabedaten lesen'.
3. Der Controller ruft `put(key, value)` auf dem `Dictionary` auf.
4. In der `Dictionary`-Swimlane wird 'Pfad im B+-Baum suchen' und 'Passenden Block laden' ausgeführt.
5. Das Dictionary ruft `readBlock(blockId)` auf dem `Store` auf.
6. Der `Store` liest den Block und gibt ihn zurück. Die Dictionary-Swimlane führt 'Eintrag im Block aktualisieren' aus und ruft `writeBlock(blockId, blockData)` auf dem `Store` auf.
7. Nach erfolgreichem Schreiben gibt das Dictionary `true` an den Controller zurück, der 'Erfolg anzeigen' ausführt.
- **Theoretischer Bezug:** [[Kapitel_16__GUI-Anbindung_und_Persistenz]]
- **Stolpersteine / Fehlerquellen:** Falsche Zuweisung der Aktionen zu den Swimlanes. Das Dictionary führt die logische Verwaltung des B+-Baums durch, der Store liest/schreibt nur rohe Blöcke.
