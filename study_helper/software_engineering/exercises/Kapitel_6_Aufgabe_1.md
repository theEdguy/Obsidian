---
id: da54ecca-245f-526e-8073-cb687e6ee2c2
title: "Kapitel_6_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - requirements
  - nfa
  - exercise
  - draft
source: "Kapitel 6 Übung"
---

# Kapitel 6 Aufgabe 1

- **Aufgabenstellung:** Welche der folgenden Anforderungen stellt eine nicht-funktionale Anforderung dar?

A) Das System muss Benutzer authentifizieren können.
B) Die Authentifizierung muss mit OAuth 2.0 erfolgen.
C) Die Authentifizierung darf maximal 5 Sekunden dauern.
D) Die Authentifizierung muss in der Datenbank gespeichert werden.
- **Lösungsweg / Musterlösung:** Richtige Antwort: C

Erklärung: NFAs beschreiben Qualitätseigenschaften. Eine Antwortzeit von 'maximal 5 Sekunden' is ein messbares Qualitätskriterium. A ist eine funktionale Anforderung (was das System tut), B und D sind technische Randbedingungen (Constraints für Protokoll und Speicherung).
- **Theoretischer Bezug:** [[Kapitel_6__Requirements]]
- **Stolpersteine / Fehlerquellen:** Verwechslung von NFAs (Qualitätseigenschaften) mit technischen Randbedingungen (Constraints/Umsetzungsvorgaben).
