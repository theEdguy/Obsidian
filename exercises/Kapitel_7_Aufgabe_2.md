---
id: 428411db-198b-5ba8-823c-8e949208bdc8
title: "Kapitel_7_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - use_cases
  - beziehungen
  - exercise
  - draft
source: "Kapitel 7 Übung"
---

# Kapitel 7 Aufgabe 2

- **Aufgabenstellung:** Ein Use Case 'Buch bestellen' soll um den Use Case 'Zahlung prüfen' erweitert werden. Welche Beziehung ist zu verwenden, wenn die Prüfung immer durchgeführt werden muss?

A) Generalisierung
B) <<extend>>
C) <<include>>
D) Assoziation ohne Stereotyp
- **Lösungsweg / Musterlösung:** Richtige Antwort: C

Erklärung: Wenn ein Anwendungsfall zwingend ein anderes Verhalten erfordert, wird dies über eine <<include>>-Beziehung modelliert. Ein <<extend>> wird verwendet, wenn das Verhalten optional bzw. bedingt ist.
- **Theoretischer Bezug:** [[Kapitel_7__Use_Cases_erstellen_und_beschreiben]]
- **Stolpersteine / Fehlerquellen:** Falsche Richtung bei extend (extend zeigt vom optionalen Zweig zum Basis-Use-Case) und Verwechslung von Pflicht (include) und Option (extend).
