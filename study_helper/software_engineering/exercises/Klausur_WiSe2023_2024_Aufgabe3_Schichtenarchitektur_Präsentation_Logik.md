---
id: 25cce9aa-2868-484c-af3c-bc5405db8775
title: "Klausur_WiSe2023_2024_Aufgabe3_Schichtenarchitektur_Präsentation_Logik"
date: 2026-05-30
tags:
  - software_engineering
  - wise2023_2024
  - klausur_ws_2023_2024
  - schichtenarchitektur
  - software_architektur
  - präsentationsschicht
  - logikschicht
  - separation_of_concerns
  - spielentwicklung
  - exercise
  - draft
source: "SWE 2023-2024 mit Loesung.pdf"
---

# [[Klausur_WiSe2023_2024_Aufgabe3_Schichtenarchitektur_Präsentation_Logik]]

- **Aufgabenstellung:** 
  - **a:** Welche Aufgaben übernehmen [[Präsentationsschicht]] und [[Logikschicht]] im Rahmen einer [[Schichtenarchitektur]]? Warum ist eine Trennung in Präsentation und Logik sinnvoll? (4 Punkte)
  - **b:**
  Ordnen Sie die folgenden Aufgaben, die für die Realisierung eines Kartenspiels wichtig sind, jeweils [[Präsentationsschicht]] und [[Logikschicht]] zu. Gibt es Aufgaben, die für beide Schichten relevant sein könnten? Gibt es Aufgaben, die keine dieser Schichten übernehmen sollte? Begründen Sie Ihre Antworten! (5 Punkte)
  
  1. Die Karten mischen
  2. Einem Spieler eine vordefinierte Anzahl an Karten zuweisen.
  3. Die nicht verteilten Karten auf einen verdeckten Stapel legen.
  4. Den Kartenbestand eines Spielers verwalten.
  5. Die oberste Karte vom verdeckten Stapel ziehen und zu den Karten eines Spielers hinzufügen.
  6. Für jeden Spieler die Karten in aufsteigender Reihenfolge sortieren.
  7. Jedem Spieler die Möglichkeit bieten, die eigenen Karten in einer bevorzugten Reihenfolge anzuordnen.
  8. Den Spielern die Möglichkeit geben, zwischen unterschiedlichen Kartendesigns zu wählen.
  9. Entscheiden, ob es besser ist, eine Karte auszuspielen oder aufzunehmen.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **aufgaben_präsentationsschicht:** Die [[Präsentationsschicht]] realisiert die [[Schnittstelle]] zum Anwender. Sie visualisiert den internen Zustand des Systems, stellt Ergebnisse dar und nimmt Eingaben entgegen, die sie an die [[Logikschicht]] weiterleitet.
    - **aufgaben_logikschicht:** Die [[Logikschicht]] kapselt die eigentliche Anwendung und bildet den funktionalen Kern der Lösung. Sie implementiert die [[Geschäftslogik]] und führt die vom Anwender initiierten Operationen aus.
    - **begründung_trennung:**
  Eine strikte Trennung von [[Präsentationsschicht]] und [[Logikschicht]] ermöglicht:
  - Einfaches Austauschen oder Anpassen der [[Benutzeroberfläche]] (z. B. Internationalisierung, Anpassung an Kundenwünsche).
  - Wiederverwendbarkeit der [[Geschäftslogik]] in unterschiedlichen Kontexten (z. B. Desktop-, Web- oder Mobile-Anwendung).
  - Bessere Wartbarkeit und Testbarkeit, da die Schichten unabhängig voneinander entwickelt und geprüft werden können.
  - [[Lose_Kopplung]] zwischen Darstellung und Logik, was die Flexibilität und Erweiterbarkeit des Systems erhöht.
  - **b:**
  - **logikschicht:**
  - **aufgaben:**
  - 1
        - 2
        - 3
        - 4
        - 5
      - **begründung:** Diese Aufgaben sind Teil der [[Spielregeln]] und der [[Geschäftslogik]]. Sie definieren den funktionalen Kern des Kartenspiels und müssen unabhängig von der Darstellung implementiert werden. Visualisierungen oder Animationen dieser Vorgänge (z. B. das grafische Mischen der Karten) gehören jedoch zur [[Präsentationsschicht]].
    - **präsentationsschicht:**
  - **aufgaben:**
  - 7
        - 8
      - **begründung:** Diese Aufgaben dienen ausschließlich der Darstellung und Interaktion mit dem Anwender. Sie haben keinen Einfluss auf die [[Spielregeln]] oder den Spielablauf und sind daher der [[Präsentationsschicht]] zuzuordnen.
    - **abhängig_vom_kontext:**
  - **aufgabe:** 6
      - **begründung:**
  Die Sortierung der Karten in aufsteigender Reihenfolge kann entweder der [[Logikschicht]] oder der [[Präsentationsschicht]] zugeordnet werden:
  - **Logikschicht**: Falls die Sortierung für die [[Spielregeln]] oder die [[Geschäftslogik]] relevant ist (z. B. wenn die Reihenfolge der Karten den Spielablauf beeinflusst).
  - **Präsentationsschicht**: Falls die Sortierung nur der besseren Übersichtlichkeit für den Anwender dient und keine Auswirkungen auf den Spielablauf hat.
    - **keine_der_schichten:**
  - **aufgabe:** 9
      - **begründung:** Diese Entscheidung obliegt dem Spieler und ist weder Teil der [[Geschäftslogik]] noch der Darstellung. Sie wird außerhalb der [[Schichtenarchitektur]] getroffen und könnte beispielsweise durch eine [[KI-Komponente]] oder direkt durch den Anwender realisiert werden.
- **Theoretischer Bezug:** 
  - [[Schichtenarchitektur]]
  - [[Präsentationsschicht|Präsentationsschichten]]
  - [[Logikschicht|Logikschichten]]
  - [[Geschäftslogik]]
  - [[Schnittstelle|Schnittstellen]]
  - [[Lose_Kopplung]]
  - [[Spielregeln]]
  - [[Benutzeroberfläche]]
  - [[Separation_of_Concerns]]
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von [[Präsentationsschicht]] und [[Logikschicht]]: Häufig werden Aufgaben der [[Geschäftslogik]] fälschlicherweise in die [[Präsentationsschicht]] verlagert, was zu schwer wartbarem Code führt.
  - Unklare Zuordnung von Aufgaben, die sowohl Darstellung als auch Logik betreffen (z. B. Sortierung der Karten). Hier muss der Kontext der [[Spielregeln]] genau analysiert werden.
  - Annahme, dass alle Entscheidungen des Spielers in die [[Logikschicht]] gehören. Strategische Entscheidungen (z. B. welche Karte gespielt wird) sind oft außerhalb der [[Schichtenarchitektur]] angesiedelt.
  - Vernachlässigung der [[Separation_of_Concerns]]: Die strikte Trennung der Schichten wird nicht konsequent umgesetzt, was die Wiederverwendbarkeit und Testbarkeit des Systems beeinträchtigt.
  - Übersehen von Visualisierungsaspekten: Auch wenn eine Aufgabe (z. B. Karten mischen) der [[Logikschicht]] zugeordnet wird, können Animationen oder grafische Darstellungen dieser Aufgabe in die [[Präsentationsschicht]] fallen.
