---
id: ec1f8119-083f-5fb6-a0b5-7f3e96c65752
title: "Kapitel_14_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - entwurfsmuster
  - abstract_factory
  - exercise
  - draft
source: "Kapitel 14 Übung"
---

# Kapitel 14 Aufgabe 1

- **Aufgabenstellung:** Welches der folgenden Szenarien beschreibt einen typischen Anwendungsfall für die Abstrakte Fabrik (Abstract Factory)?

A) Ein Texteditor soll zur Laufzeit zwischen verschiedenen Betriebssystem-Stilen (Windows/macOS/Linux) wechseln können.
B) Ein Datenbank-Client soll automatisch zwischen MySQL und PostgreSQL umschalten, wenn eine Verbindung fehlschlägt.
C) Ein Spiel soll zufällig Gegner-Charaktere mit unterschiedlichen Fähigkeiten generieren.
D) Ein Compiler soll während der Kompilierung temporäre Dateien für die Zwischenspeicherung nutzen.
- **Lösungsweg / Musterlösung:** Richtige Antwort: A

Erklärung: Die Abstrakte Fabrik wird eingesetzt, wenn Familien verwandter Objekte (hier: plattformspezifische UI-Komponenten wie Button, TextField für ein bestimmtes OS) konsistent erzeugt werden müssen und der Client unabhängig von konkreten Implementierungen arbeiten soll.
- **Theoretischer Bezug:** [[Kapitel_14__Patterns_–_Erzeugungsmuster]]
- **Stolpersteine / Fehlerquellen:** Verwechslung mit der einfachen Fabrikmethode (die einzelne Objekte erzeugt, nicht Familien) oder dem Strategie-Muster.
