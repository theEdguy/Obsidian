---
id: bff35cb9-1e31-5e69-a237-34f58e144e78
title: "Kapitel_15_Aufgabe_2"
date: 2026-06-20
tags:
  - software_engineering
  - klausur_vorbereitung
  - entwurfsmuster
  - adapter
  - exercise
  - draft
source: "Kapitel 15 Übung"
---

# Kapitel 15 Aufgabe 2

- **Aufgabenstellung:** Ein Entwickler möchte eine neue Verschlüsselungs-API in ein bestehendes System integrieren. Die neue API hat jedoch eine andere Schnittstelle als die vom System geforderte Schnittstelle 'Cipher'. Welches Muster sollte er verwenden?

A) Bridge, um Abstraktion und Implementierung zu trennen.
B) Adapter, da er die inkompatible Schnittstelle der API an das geforderte 'Cipher'-Interface anpasst.
C) Singleton, um nur eine API-Instanz zu erlauben.
D) Decorator, um das Verhalten der API zu erweitern.
- **Lösungsweg / Musterlösung:** Richtige Antwort: B

Erklärung: Das Adapter-Muster ist ideal, um bestehende Komponenten mit inkompatiblen Schnittstellen nutzbar zu machen. Der Adapter implementiert das System-Interface 'Cipher' und leitet die Aufrufe an die neue API weiter.
- **Theoretischer Bezug:** [[Kapitel_15__Patterns_–_Strukturmuster]]
- **Stolpersteine / Fehlerquellen:** Sich von der Bridge ablenken lassen, die für das bewusste Aufteilen eigener Klassen gedacht ist, nicht für das Verpacken fremder APIs.
