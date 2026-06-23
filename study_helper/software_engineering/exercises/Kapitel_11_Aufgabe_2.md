---
id: acf8fcbe-92b3-54ab-b42d-bba2c1042fe6
title: "Kapitel_11_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - observer
  - entwurfsmuster
  - exercise
  - draft
source: "Kapitel 11 Übung"
---

# Kapitel 11 Aufgabe 2

- **Aufgabenstellung:** Welche Methode gehört typischerweise NICHT zu den Schnittstellenoperationen des Subjekts im Observer-Muster?

A) attach(Observer)
B) detach(Observer)
C) notify()
D) handleEvent()
- **Lösungsweg / Musterlösung:** Richtige Antwort: D

Erklärung: attach, detach und notify sind die typischen Operationen des Subjekts zur Verwaltung und Benachrichtigung von Beobachtern. handleEvent() ist eine Methode des Controllers zur Verarbeitung von Benutzeraktionen.
- **Theoretischer Bezug:** [[Kapitel_11__MVC-Architektur_und_das_Observer-Muster]]
- **Stolpersteine / Fehlerquellen:** Verwechslung des Controller-Verhaltens (Eingabe) mit dem Subjekt-Verhalten (Zustandsänderung).
