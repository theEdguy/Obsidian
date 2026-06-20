---
id: 15297738-1635-5437-849d-b4ea7d8fcde4
title: "Kapitel_14_Aufgabe_2"
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

# Kapitel 14 Aufgabe 2

- **Aufgabenstellung:** Welcher der folgenden Nachteile ist typisch für die Abstrakte Fabrik, aber nicht für die einfache Fabrikmethode?

A) Erhöhte Komplexität durch zusätzliche Abstraktionsschichten.
B) Starke Kopplung zwischen Client und konkreten Produkten.
C) Unfähigkeit, neue Produkttypen zur Laufzeit hinzuzufügen.
D) Die Notwendigkeit, bei der Einführung neuer Produkttypen die Schnittstelle der abstrakten Fabrik und alle konkreten Fabrikunterklassen zu ändern.
- **Lösungsweg / Musterlösung:** Richtige Antwort: D

Erklärung: Da die Abstrakte Fabrik Schnittstellen für die Erzeugung einer festen Produktfamilie bereitstellt, muss bei Einführung eines neuen Produkts (z. B. VideoLabel) das Interface LabelFactory sowie jede konkrete Fabrikklasse (GermanLabelFactory, USLabelFactory) angepasst werden (Verletzung des Open/Closed-Prinzips).
- **Theoretischer Bezug:** [[Kapitel_14__Patterns_–_Erzeugungsmuster]]
- **Stolpersteine / Fehlerquellen:** Vergessen, dass die Produktpalette bei einer Abstrakten Fabrik fest vorgegeben ist, während neue Familien leicht durch neue Fabriken ergänzt werden können.
