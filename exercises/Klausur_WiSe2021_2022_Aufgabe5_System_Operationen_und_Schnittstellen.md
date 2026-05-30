---
id: ebd913e3-20a3-474e-b9bd-c79ed0fadbc0
title: "Klausur_WiSe2021_2022_Aufgabe5_System_Operationen_und_Schnittstellen"
date: 2026-05-30
tags:
  - software_engineering
  - wise2021_2022
  - klausur_ws2021_2022
  - systemdesign
  - schnittstellen
  - zustandsdiagramme
  - operationen
  - aufgabenverteilung
  - prüfungsvorbereitung
  - exercise
  - draft
source: "SWE 2021-2022 mit Loesung.pdf"
---

# [[Klausur_WiSe2021_2022_Aufgabe5_System_Operationen_und_Schnittstellen]]

- **Aufgabenstellung:** 
  Gegeben sind zwei Abbildungen (hier nicht visualisiert) als Teil des Designs eines Systems. Ihre Aufgaben sind:
  
  1. Bestimmen Sie, wie viele [[Operation|Operationen]] rein schematisch der [[Schnittstelle|Schnittstelle]] 'I' zugeordnet werden können.
  
  2. Ordnen Sie jeder identifizierten [[Operation]] diejenigen Aufgaben (Nummern 1 bis 10) zu, für deren korrekte Durchführung sie verantwortlich ist. Die Aufgaben sind durch Zustandsübergänge im System definiert:
     - Operation 1: Übergang von Zustand 1 zu Zustand 2
     - Operation 2: Übergang von Zustand 6 zu Zustand 7
  
  3. Geben Sie an, welche Aufgaben (Nummern) den jeweiligen Operationen zugeordnet sind. Beachten Sie, dass bei falscher Zuordnung (zu viele oder zu wenige Aufgaben) Abzüge von 0,5 Punkten pro Fehler vorgesehen sind.
- **Lösungsweg / Musterlösung:** 
  1. **Anzahl der Operationen in der Schnittstelle 'I':**
     - Rein schematisch können der [[Schnittstelle|Schnittstelle]] 'I' **zwei [[Operation|Operationen]]** zugeordnet werden. Diese ergeben sich aus den beschriebenen Zustandsübergängen:
       - Operation 1: Übergang 1 → 2
       - Operation 2: Übergang 6 → 7
  
  2. **Zuordnung der Aufgaben zu den Operationen:**
     - **Operation 1 (Übergang 1 → 2):** Verantwortlich für die Aufgaben **2, 4, 5**.
       - *Hinweis:* Bei falscher Zuordnung (z. B. zusätzliche oder fehlende Aufgaben) erfolgt ein Punktabzug von 0,5 Punkten.
  
     - **Operation 2 (Übergang 6 → 7):** Verantwortlich für die Aufgaben **7, 10, 8, 5**.
       - *Hinweis:* Auch hier führt eine falsche Zuordnung zu einem Punktabzug von 0,5 Punkten pro Fehler.
- **Theoretischer Bezug:** 
  Diese Aufgabe bezieht sich auf folgende Konzepte:
  - [[Schnittstelle|Schnittstellen]] im [[Klassendiagramm|Klassendiagramm]]
  - [[Operation|Operationen]] und deren Verantwortlichkeiten im Systemdesign
  - [[Zustandsdiagramm|Zustandsdiagramme]] zur Modellierung von Zustandsübergängen
  - [[Systemverhalten]] und [[Aufgabenverteilung]] in der [[Softwarearchitektur]]
  - [[Kohäsion]] und [[Kopplung]] bei der Zuordnung von Verantwortlichkeiten zu [[Operation|Operationen]]
- **Stolpersteine / Fehlerquellen:** 
  - 1. **Fehlinterpretation der Zustandsübergänge:** Verwechslung der Zustandsnummern oder falsche Zuordnung der Übergänge zu den [[Operation|Operationen]]. Beispiel: Annahme, dass mehr als zwei [[Operation|Operationen]] existieren könnten.
  - 2. **Über- oder Unterzuordnung von Aufgaben:** Zu viele oder zu wenige Aufgaben einer [[Operation]] zuordnen, was zu Punktabzügen führt. Besonders kritisch ist die Aufgabe 5, die beiden [[Operation|Operationen]] zugeordnet ist.
  - 3. **Vernachlässigung der Abzugsregel:** Nicht beachten, dass falsche Zuordnungen (auch bei korrekter Anzahl) zu Punktabzügen führen. Dies erfordert präzises Arbeiten.
  - 4. **Unklare Trennung von [[Schnittstelle|Schnittstellen]] und Implementierung:** Verwechslung der schematischen Zuordnung von [[Operation|Operationen]] zu einer [[Schnittstelle]] mit deren konkreter Implementierung in einer Klasse.
  - 5. **Missverständnis der Aufgabenstellung:** Annahme, dass die Abbildungen (hier nicht vorhanden) zusätzliche Hinweise liefern, obwohl die Lösung rein auf den gegebenen Textinformationen basiert.
