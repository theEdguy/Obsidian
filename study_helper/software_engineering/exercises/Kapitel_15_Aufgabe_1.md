---
id: bd106f6d-2341-5795-86a5-7cefd94da329
title: "Kapitel_15_Aufgabe_1"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - entwurfsmuster
  - bridge
  - adapter
  - exercise
  - draft
source: "Kapitel 15 Übung"
---

# Kapitel 15 Aufgabe 1

- **Aufgabenstellung:** Welcher der folgenden Punkte beschreibt einen wesentlichen konzeptionellen Unterschied zwischen dem Bridge-Muster und dem Adapter-Muster?

A) Der Adapter wird zur Laufzeit eingesetzt, die Bridge nur zur Compilezeit.
B) Der Adapter dient dem nachträglichen Auflösen von Schnittstelleninkompatibilitäten unabhängig entworfener Klassen (post-facto), während die Bridge von vornherein (up-front) entworfen wird, um Abstraktion und Implementierung unabhängig variieren zu lassen.
C) Die Bridge ändert die Schnittstelle einer Klasse, während der Adapter nur die Implementierung anpasst.
D) Das Adapter-Muster erfordert immer Mehrfachvererbung, während die Bridge dies verbietet.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Dies ist der entscheidende Unterschied. Der Adapter ist ein Wrapper für inkompatiblen Code (oft Legacy-Code oder Drittbibliotheken). Die Bridge hingegen ist ein Entwurfsstrukturmuster, das up-front geplant wird, um Abstraktion und Implementierung getrennt weiterzuentwickeln.
- **Theoretischer Bezug:** [[Kapitel_15__Patterns_–_Strukturmuster]]
- **Stolpersteine / Fehlerquellen:** Beide Muster leiten Anfragen an ein anderes Objekt weiter und führen eine Indirektion ein, was oft zu Verwechslungen führt.
